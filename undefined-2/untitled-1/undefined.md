# \[리액트\] 바인딩

참고 : 해당 내용은 리액트 도움 닫기를 참고하여 내용을 기술 하였습니다. 

\(문제가 될 시 삭제 하도록 하겠습니다.\)

this.onChangeMethod = this.onChangeMethod.bidn\(this\)

클래스에 바인딩이 되어 있으므로 클래스 메서드!!

onChangeMethod가 아니라 this.onChangeMethod 로 접근!!

this는 클래스 인스턴스 !!

onChangeMethod를 클래스 메서드로 정의하기 위해서는 생성자에서 바인딩!!!!!!!!!

ES6에서의 클래스 메서드 바인딩

contructor\(props \){

super\(props\);

this.onDismiss = this.onDismiss.bind\(this\);

}

&gt;&gt;  처음부터 바인딩을 한 이유 ?

클래스 메서드는 클래스 인스턴스에 자동으로 this를 바인딩하지 않기 때문에 일일이 바인딩을 해줘야함.

--

class eventBindingsComponent extends Component{

onClickMe\(\){

console.log\(this\);

}

render\(\){

return \(

&lt;button 

onClick={this.onClickMe}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

위의 코드는 렌더링은 잘 되지만 버튼을 클릭하면 개발자 콘솔로그에 undefined가 출력됨.

클래스 메서드에서 this.state에 접근하고자 할 때 this가 undefined이면 접근할 수 없음.

클래스 메서드에서 this를 접근할 수 있게 하려면 클래스 메서드를 this 에 바인딩 해야함.

class eventBindingsComponent extends Component{

constructor\(\) {

this.onClickMe = this.onClickMe.bind\(this\);

}

onClickMe\(\){

console.log\(this\);

}

render\(\){

return \(

&lt;button 

onClick={this.onClickMe}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

버튼을 만들 때, 클래스 인스턴스를 구체적으로 지정하기 위해 this 객체를 정의한 후, this.state에 접근하거나, this.props를 사용해 접근해야 함.

클래스 메서드 바인딩은 어느 곳에서든지 사용할 수 있음.

클래스 메서드인 render\(\)안에서도 사용할 수 있음.

class eventBindingsComponent extends Component {

onClickMe\(\){

console.log\(this\);

}

render\(\){

return \(

&lt;button 

onClick={this.onClickMe.bond\(this\)}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

render\(\)메서드가 실행딜 때마다 클래스 메서드를 바인드 하기 때문에, 컴포넌트가 업데이트 될 때마다 실행되어 성능에 영향을 미치게 됨.

render\(\) 메서드에서 바로 바인딩을 하지 않는 편이 좋음.

생성자에서 클래스 메서드를 바인딩해 컴포넌트가 인스턴스와 될 때 처음에 한 번만 바인딩하는 것이 더 좋은 방법임.

생성자에서 바로 클래스 메서드의 할 일을 정의할 수도 있음.

  
class eventBindingsComponent extends Component{

constructor\(\) {

this.onClickMe = \(\)=&gt;{

console.log\(this\);

}

}

render\(\){

return \(

&lt;button 

onClick={this.onClickMe}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

하지만 생성자에게 혼란을 줄 수 있으므로 사용하지 않는 것이 좋음.

생성자는 클래스의 모든 프로퍼티를 인스턴스화 하기 위해 존재함.

클래스 메서드의 로직은 생성자와 외부에서 정의하는 것이 좋음.

class eventBindingsComponent extends Component{

constructor\(\) {

this.something = this.something.bind\(this\);

}

something\(\){

console.log\(this\);

}

render\(\){

return \(

&lt;button 

onClick={this.something}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

화살표 함수를 사용하여 클래스 메서드를 생성자 내부에 바인딩하지 않고도 자동 바인딩할 수 있음.

class eventBindingsComponent extends Component{

this.something = this.something.bind\(this\);

something=&gt;\(\)=&gt; {

console.log\(this\);

}

something\(\){

console.log\(this\);

}

render\(\){

return \(

&lt;button 

onClick={this.something}

type="button"

&gt;

Click Me

&lt;/button&gt;

\);

}

}

클래스 메서드마다 생성자에 바인딩 처리가 번거롭기 때문에 위 방법 ..

리액트 공식 문서에서는 생성자 내부에 클래스 메서드를 바인딩할 것을 제안하고 있음.

