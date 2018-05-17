# \[ES6\] 클래스

[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)

참고 : 해당 내용은 리액트 도움 닫기 및 mdn을 참고하여 내용을 기술 하였습니다. 

\(문제가 될 시 삭제 하도록 하겠습니다.\)

리액트는 불변하는 데이터 구조를 다룰 때는 함수형 프로그래밍을,

컴포넌트를 만들 때는 클래스로 선언함.

**Class선언** 

class User {

constructor\(name, age\){

this.name=name;

this.age=age;

}

getUser\(\){

return this.name + this.age;

}

}

class를 정의하는 한 가지 방법은 class 선언을 이용하는 것임. 

class를 선언하기 위해서는 클래스 이름과 함께 class 키워드를 사용함.

참고\)

함수 선언과 클래스 선언의 중요한 차이점은 함수 선언의 경우 호이스팅이 일어나지만, 클래스 선언은 그렇지 않음.

클래스를 사용하기 위해서는 클래스를 먼저 선언 해야 하며, 그렇지 않으면 ReferenceError 에러를 던짐.

```javascript
var p = new User(); // ReferenceError
class User{}
```

**Class 표현식**

class를 정의하는 또 다른 방법임.

이름을 가질 수도 있고, 갖지 않을 수도 있음.

기명 class 표현식에 주어진 이름은 클래스의  body에 대해 local scope에 한해 유효함.

```javascript
// unname
var User = class {
    constrouctor(firstName, lastName){
        this.firstName=firstName;
        this.lastName=lastName;
    }
};

// named
var User = class User {
    constrouctor(firstName, lastName){
        this.firstName=firstName;
        this.lastName=lastName;
    }
}
```

**Class body와 method정의**

Class body는 중괄호 {}로 묶여 있는 안쪽 부분임. method나 constructor와 같은 class members를 정의하는 곳임.

**Strict mode**

클래스 선언과 클래스 표현식의 본문은 strict mode에서 실행됨.

**constructor &gt;&gt; 인스턴스화 할 수 있는 생성자.**

constructor 메소드는 class로 생성된 객체를 생성하고 초기화 하기 위한 특수한 메소드 임.

constructor라는 이름을 가진 특수한 메소드는 클래스 안에 한 개만 존재할 수 있음.

만약 클래스에 한 개를 초과하는 constructor메소드를 포함한다면, syntaxError가 발생함.

constructor는 부모 클래스의 contructor를 호출하기 위해 super키워드를 사용할 수 있음. 

```javascript
class User {
    constructor(firstName, lastName){
        this.firstName = firstName;
        this.lastName = lastName;
    }
    get info (){
        return this.concatText();
    }
    
    concatText(){
        return this.firstName+this.LastName;
    }
}
const users=new User("mon","day");
console.log(users.info);
```



생성자는 매개변수를 사용해 클래스 인스턴스에 할당함.

클래스는 함수를 정의함.

함수는 클래스와 연관되어 있어 메서드라고도 불림.

이 메서드는 클래스 메서드로 참조됨.

User클래스는 클래스 선언문일 뿐임.

클래스를 호출해 클래스 내 여러 인스턴스를 작성할 수 있음.

const user1=new User\('kim','22'\);

console.log\(user1.getUser\(\)\);

**클래스의 확장 ? \(extends를 통한 클래스 상속\)**

객체 지향 프로그래밍에는 상속의 원칙이 있음. 

한 클래스의 기능을 다른 클래스로 전달하는데 사용됨.

extends 키워드는 클래스 선언이나 클래스 표현식에서 다른 클래스의 자식 클래스를 생성하기 위해 사용됨.

```javascript
class Product {
    constructor(name,price){
        this.name=name;
        this.price=price;
    }
    
    publish(){
        console.log('This product is published by builder');
    }
}

class Package extends Product {
    publish() {
        console.log(this.name+' is published.');
    }
}

//var prod = new Product('picture',10000000);
//prod.publish();
var pack = new Package('movie',2000000);
pack.publish();
```

subclass에 constructor가 있다면 , "this"를 사용하기 전에 가장 먼저 super\(\)를 호출해야함.



ES6 클래스 컴포넌트에 생성자가 있으면 super\(\)호출을 해야함.

super를 통한 상위 클래스 호출

```javascript
class Product {
    constructor(name, price){
        this.name=name;
        this.price=price;
    }
    
    publish(){
        console.log('This product is published by builder');
    }
}

class Package extends Product {
    publish() {
        super.publish();
        console.log(this.name+' is published.');
    }
}
var pack = new Package('movie',2000000);
pack.publish();
```

객체의 부모가 가지고 있는 함수들을 호출하기 위해 사용됨.



추가적으로 필요한 키워드, 개

* static 키워드

