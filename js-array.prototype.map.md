# \[JS\] Array.prototype.map\(\)

{% embed data="{\"url\":\"https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/map\",\"type\":\"link\",\"title\":\"Array.prototype.map\(\)\",\"description\":\"map\(\) 메소드는 배열 내의 모든 요소 각각에 대하여 제공된 함수\(callback\)를 호출하고, 그 결과를 모아서, 새로운 배열을 반환합니다.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.mozilla.org/static/img/favicon144.e7e21ca263ca.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.mozilla.org/static/img/opengraph-logo.72382e605ce3.png\",\"width\":600,\"height\":600,\"aspectRatio\":1}}" %}

해당 문서를 참고 하였습니다.

 **간단 설명**

배열 내의 모든 요소 각각에 대하여 제공된 함수\(callback\)를 호출하고, 그 결과를 모아서 **새로운 배열을 반환**합니다. 

**구문**

var new\_array=arr.map\(function callback\(currentValue\[, index\[, array\]\]{

// new\_array 의 새 요소 반환

}\[,thisArg\]\)

**파라미터**

callback

-currentValue

-index

-array

thisArg

**설명**

callback함수를 각각의 요소에 대하 한번씩 순서대로 불러 그 함수의 리턴값\(결과값\)으로 새로운 배열을 만듭니다. 

callback함수는 \(undefined 포함\) 배열 값이 들어 있는 인덱스에 대해서만 호출됩니다. 값이 삭제 되거나 아직 값이 할당/정의 되지 않는 인덱스에 대해서는 호출되지 않습니다. 

callback함수가 호출 될 때에는, 호출되는 대상 요소의 값, 그 요소의 인덱스 그리고 map 메소드가 사용된 배열 객체의 3개의 인수를 전달 받습니다. 

thisArg 매개변수가 map에 전달될 때에는, callback함수의 this값으로 사용됩니다. 

그 외의 경우 undefined값이 this값으로 사용됩니다. 

callback함수에서 최종적으로 볼 수 있는  this값은 부른 함수에 따라 결정됩니다. 

map은 호출된 배열의 값을 변형되지 않습니다. \(callback함수 호출에 따라 변형이 이뤄질 수는 있습니다.\)

map은 호출된 배열의 값을 변형하지 않습니다. \(단, callback 함수 호출에 의해서 변경될 수는 있습니다.\)

map이 처리할 요소들의 범위는 첫 callback을 실행하기 전에 설정됩니다. 

map이 시작된 이후 배열에 추가된 요소들은 callback이 호출되지 않습니다.  배열에 존재하던 요소들의 값이 바뀌는 경우, map이 방문하는 시점의 값이 callback에 전달됩니다. 

map이 시작되고 map이 방문하기 전에 삭제된 요소들은 방문하지 않습니다. 

map이 호출된 배열이 드문드문 비어 있는 경우, 결과 또한 동일한 인덱스를 빈 값으로 유지한 배열이 됩니다.

**예제**

1\) 배열에 들어 있는 숫자들의 제곱을 구하여 새로운 배열을 만듭니다.

```text
var numbers = [1,2,3,4,5];var new_array = numbers.map(function(val) {	return val*val;});console.log(numbers);console.log(new_array);
```

numbers는 변하지 않고,  new\_array는 새로운 배열을 리턴한 것을 볼 수 있습니다.

2\) map을 활용해 오브젝트를 다시 재구성하기

```javascript

```



