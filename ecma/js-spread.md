# \[ES6\] spread 연산자\(전개 연산자\)

{% embed url="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread\_operator" %}

ECMAScript6길들이기 책들을 참고하여 정리 하였습니다. 



2개 이상의 인수\(함수 호출용\)는 2개 이상의 요소\(배열 리터럴용\) 또는 2개 이상의 변수\(비구조화 할당용\)가 예상되는 곳에 확장될 수 있도록 함.

문법

1\) 함수 호출용

```javascript
const listObj=[
    {
        id : 1,
        subject : 'text1'
    },
    {
        id : 2,
        subject : 'text2'
    }
]
myPosting(...listObj);
```

2\) 배열 리터럴 용

```javascript
const listObj=[
    {
        id : 1,
        subject : 'text1'
    },
    {
        id : 2,
        subject : 'text2'
    }
];

[...listObj,
{
    id : 3,
    subject : 'text3'
}];
```

3\) 비구조화 할당 용

```javascript
[post1,post2,...listObj]=[
    {
        id : 1,
        subject : 'text1'
        },
    {
        id : 2,
        subject : 'text2'
        },
    {
        id : 3,
        subject : 'text3'
        },
    {
        id : 4,
        subject : 'text4'
        },
    {
        id : 5,
        subject : 'text5'
        },
    {
        id : 6,
        subject : 'text6'
    }
];

console.log(post1);
console.log(post2);
console.log(listObj);
```

예전에는 배열을 함수의 인자로 사용하고 싶을 때는 apply를 사용하였지만 전개연산자를 사용하여 배열을 함수의 인자로 사용할 수 있음.

```javascript
function myProduct(x,y,z){}
var args=['paper','pencile','water'];
myProduct.apply(null,args);
```

\(예전\)

```javascript
function myProduct(x,y,z){}
var args=['paper','pencile','water'];
myProduct(...args);
```

\(es6\)

인수 목록의 어떤 인수라도 전개 연산자 구문을 쓸 수 있고 여러번 사용될 수 있음.

```javascript
function myProduct(v,w,x,y,z){}
var args=['paper','pencile'];
myProduction(-1,...args,2,...[4]);
```



