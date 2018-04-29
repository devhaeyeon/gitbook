# \[리액트\] 이벤트 핸들러

  
일반적으로  render\(\) 밖에서 이벤트 핸들러에 전달되는 함수를 만들어야함. 

애플리케이션이 구동되면 클래스 메서드가 즉시 실행되기 때문에 코드는 작동하지 않음.

&lt;button 

onClick={this.onClickMe.bond\(this\)}

type="button"

&gt;

Click Me

&lt;/button&gt;

onClick={something\(\)}일 경우, something\(\)함수는 그 즉시 실행됨.

핸들러 표현식이 평가 되는데, 그 결과를 함수로 반환하지 않기 때문에 버튼을 클릭해도 아무 일이 일어나지 않음.

onClick={something}으로 수정하면 실행됨.

이벤트 핸들러 내 화살표 함수 사용은 성능 문제와 연관됨.

onClick={\(\)=&gt;this.onClickMe\(item.objID\)}

onClickMe\(\)so onClick핸들러는 식별자를 전달하고자 다른 화살표 함수로 ㅁ서드를 래핑함.

render메서드가 실행될 때마다 핸들러는 고차 함수인 화살표 함수를 인스턴스화 함.

애플리케이션 성능에 영향을 미칠 수 있지만, 실제로 그 효과를 파악할 수 없음.

1000개의 아이템마다 이벤트 핸들러에 화살표 함수가 있다고 가정.

성능에 영향을 미치지 않게 생성자에서 메서드를 바인딩할 수 있을 것.  


