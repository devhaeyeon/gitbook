# \[ES6\] 객체 초기자\(Object Initializer\)

참고 : 해당 내용은 리액트 도움 닫기를 참고하여 내용을 기술 하였습니다. 

\(문제가 될 시 삭제 하도록 하겠습니다.\)

객체 프로퍼티 축약

기존 

const name = 'kim';

const user={

**name:**name,

}

ES6

객체 프로퍼티 이름과 변수 이름이 같다면, 하나로 축약해 정의함.

const name='kim';

const user = {

name,

}

객체 메서드 축약

기존 

var user = {

getUser : **function**\(user\){

return user.firstName + user.lastname;

}

}

ES6

const user={

getUserName\(user\) {

return user.firstname + user.lastname;

},

}

계산된 프로퍼티 이름을 사용할 수 있음.

var user = {

name :'kim',

}

const key = 'name';

const user= {

\[key\] : 'kim',

}

계산된 프로퍼티 이름은 키를 사용해 객체에서 동적인 방식으로 값을 할당할 때.

자바스크립트에서 룩업테이블\(주어진 연산에 대해 미리 계산된 결과들을 배열\)을 생성하면 코드 가독성이 높아짐.

