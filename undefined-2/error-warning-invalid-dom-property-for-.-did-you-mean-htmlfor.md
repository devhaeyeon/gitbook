# \[error\] Warning: Invalid DOM property \`for\`. Did you mean \`htmlFor\`?

리액트를 공부하다 

일반적으로 label을 마크업할 때 \(리액트를 적용하지  않은\) 

for이라는 속성값을 준다. 

```markup
<label for="nameInput"></label>
<input id="nameInput"/>
```

label을 마크업할 때처럼 리액트에 적용을 하였더니

콘솔

**Warning: Invalid DOM property \`for\`. Did you mean \`htmlFor\`?**

새빨간 경고문이 떠서 구글링을 하였더니 

리액트에서는 for가 htmlFor로 표기한다고 한다.

\(유.레.카 ...\)

{% embed data="{\"url\":\"https://reactjs.org/docs/accessibility.html\",\"type\":\"link\",\"title\":\"Accessibility - React\",\"description\":\"A JavaScript library for building user interfaces\",\"icon\":{\"type\":\"icon\",\"url\":\"https://reactjs.org/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://reactjs.org/logo-og.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

자세한 접근성 관련 마크업 내용의 리액트는 위의 링크에서 확인하면 될 것 같다.

