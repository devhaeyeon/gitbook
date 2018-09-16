# \[HTML\] 블럭 요소와 인라인 요소

마크업을 하면서 가장 많이 헷갈리는 부분이 인라인 요소와 블럭 요소이다.

'디스플레이 블록을 주었는데 왜 ? 안되지?'

이런 요소들에 대한 특성을 모르면 이런 상황이 벌어지게 되는 것 같다.

**블록 요소란 무엇일까?**

블록 요소는 HTML 문서 상에 전체적인 흐름을 차지하는 컨텐츠이다.

**특징**

1\) 블록 요소 안에 블록, 인라인 모두 포함 시킬 수 있다.

2\) p태그는 블록 요소이지만 태그 안에 p태그가 들어오면 안된다.

3\) 영역

지정 값 또는 지정 안할 시 너비는 부모의 가로 크기, 세로는 컨텐츠 크기

4\) 정렬

margin\(auto\), padding\(테이블 내의 경우 vertical-align\)

5\) 박스 모델

margin\(auto 불가\),padding, border, float

6\) 중첩 요소

인라인, 블록 모두 가능

7\) 양 옆에 요소를 둘 수 없다.

**요소의 종류**

article, fieldset, aside, figcaption, blockquote, figure, body, footer, br, form, br, button, h1~h6, canvas, head, caption, col. hgroup, colgroup, hr, dd, li, div, map, dl, object, dt, ol, embed, output, p, pre, progress, section, table, tbody, textarea, tfoot, th, thead, tr, ul, video

**인라인 요소란 무엇일까?**

인라인 요소는 행, 블록 내부의 요소이다.

**특징**

1\) 인라인 요소 안에는 블록 요소가 들어올 수 없다.

2\) 인라인 요소 안에는 인라인 요소만 쓸 수 있다.

3\) 영역

컨텐츠 크기 만큼

4\) 정렬

텍스트 정렬에 영향을 받음\(텍스트의 위치를 지정하는 모든 속성\)

5\) 박스 모델

margin-left, right/ padding, border, float

6\) 중첩 요소

인라인만 가능

**요소 들의 종류**

a, i, q, abbr, iframe, small, address, img, select, area, input, source, audio, ins, span, bm, keygen, strong, cite, kbd, sub, code, label, summary, del, legend, sup, details, link, tbody, dfn, mark, td, command, meter, time, em, nav, var, font, optgroup  


