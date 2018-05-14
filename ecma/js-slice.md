# \[JS\] slice

어떤 배열의 begin부터 end까지\(end는 불포함\)에 대한 shallow copy를 새로운 배열 객체로 반환함.

원본 배열은 수정되지 않는다. 

**구문**

arr.slice\(\)

arr.slice\(begin\)

arr.slice\(begin, end\)

**매개변수**

-begin

0을 시작으로 하는 추출 시작점에 대한 인덱스를 의미함.

음수 인덱스는 배열의 끝에서 부터 길이를 나타냄.

-end

추출을 종료할 0기준 인덱스. 

slice는 end인덱스를 제외하고 추출함.

음수 인덱스는 배열과 끝에서 부터 길이를 나타냄.

end가 생걀되면 slice 는 배열의 끝까지\(arr.length\)를 추출함

만약 end값이 배열의 길이보다 크다면, slice는 배열의 끝까지\(arr.length\)을 추출함.

**반환값**

추출된 요소가 포함된 새로운 배열

설명

원본을 대체하지 않음. 원본 배열에서 요소의 얕은 복사본을 반환함.

원본 배열 요소는 

객체 참조\(및 실제 객체가 아님\)의 경우 slice는 객체 참조를 새 배열로 복사함.

원본 배열과 새 배열은 모두 동일한 객체를 참조함.

참조된 객체가 변경되면 변경 내용은 새 배열과 원래 배열 모두 볼 수 있음 .

String 및 Number객체가 아닌 문자열과 숫자의 경우 slice는 문자열과 숫자를 새 배열에 복사함. 한 배열에서 문자열이나 숫자를 변경해도 다른 배열에는 영향을 주지 않음.

새 요소가 두 배열 중 하나에 추가되면 다른 배열은 영향을 받지 않음.

```javascript

// 슬라이스를 사용하여 내 차에서 새 차를 만듭니다.var myHonda = { color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } };var myCar = [myHonda, 2, 'cherry condition', 'purchased 1997'];var newCar = myCar.slice(0, 2);// 내 자동차, 새 자동차 및 혼다의 색상 값을 표시합니다.// 두 배열에서 모두 참조됩니다.console.log('myCar = ' + myCar.toSource());console.log('newCar = ' + newCar.toSource());console.log('myCar[0].color = ' + myCar[0].color);console.log('newCar[0].color = ' + newCar[0].color);// myHonda의 색상을 변경합니다.myHonda.color = 'purple';console.log('The new color of my Honda is ' + myHonda.color);// 두 배열에서 참조 된 myHonda의 색상을 표시합니다.console.log('myCar[0].color = ' + myCar[0].color);console.log('newCar[0].color = ' + newCar[0].color);
```









