# react에서  eslint , prettier , airbnb 적용

개발 환경  IDE : VScode

 step1. 프로젝트 디렉토리에 .eslintrc라는 파일을 만듦.

```javascript
{
    "extends":"react-app"
}
```

step2: prettier 설정

\(VSCode에서 prettier 설치\)

step3. prettier와 eslint연동하기

npm install --save prettier-eslint

CMD + , \(환경 설정\) 열어서 작업 영역\(Workspace\)에 아래를 입

```javascript
{ 
"editor.formatOnSave": true, 
"javascript.format.enable": false, 
"prettier.eslintIntegration": true 
}
```

step4. eslint 세부 설정

* 쌍따옴표 대신 일반 따옴표
* 들여쓰기 크기는 2

```javascript
{
    "extends":"react-app",
    "rules":{
        "quotes":["error","single",{"avoidEscape":true}],
        "indent":["error",2]    
    }
}
```

추가

npm install eslint-config-airbnb

```javascript
{
    "parser":"babel-eslint",
    "extends":"airbnb",
    "plugins":["react","jsx-ally","import"],
    "rules":{
        "react/jsx-filename-extension":"0"
    }
}
```

{% embed data="{\"url\":\"https://github.com/airbnb/javascript/tree/master/react\",\"type\":\"link\",\"title\":\"airbnb/javascript\",\"description\":\"javascript - JavaScript Style Guide\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars0.githubusercontent.com/u/698437?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

끄고 싶은 것들은 rules에서 0 을 주면 됨.

참고: [https://velopert.com/3671](https://velopert.com/3671)



