# \[리액트\] props

**props** 

프로퍼티의 약자로 this를 사용해 클래스 인스턴스에 접근함.

App컴포넌트에서 전달된 모든 값을 가지게 됨.

컴포넌트가 또 하위 컴포넌트로 계속해서 프로퍼티를 전달할 수 있음.

App 컴포턴트에서 뽑아낸 컴포넌트를 다른 컴포넌트 에서도 재사용할 수 있음. 

컴포넌트는 prop을 통해 값을 가져오기 때문에 props값을 바꿔 전달 할 수 있음.

함수 시그니처\(함수의 원형에 명시되는 매개변수 리스트\)에 접근할 수 있고, JSX를 반환함.

function Search\(props\){

const {value, onChange, children} = props;

....

}

위의 코드를 아래의 코드로 변경

function Search\({value, onChange, children}\) {

.,..

}

변경한 부분은 props를 입력으로 사용하고 JSX를 반환하는 경우에만 사용할 수 있음.  

