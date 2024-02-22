## ✔️ 리플로우(reflow)와 리페인팅(repaint)

- reflow와 repaint는 요소가 시각적으로 변경되었을 때, 변화를 계산하여 화면에 그려주는 작업을 말합니다.
- DOM이 시각적으로 변경되면 **reflow**가 발생하여 렌더트리를 재생성하고
- 생성된 렌더트리를 기반으로 요소를 화면에 그리는 **repaint**가 발생합니다.

## ✔️ 리플로우(reflow)

- 리플로우는 브라우저가 페이지를 렌더링할 때 발생하는 과정 중 하나로, 요소들의 크기나 위치 등이 변경될 떄 다시 계산되고 **레이아웃**이 갱신되는 과정을 말합니다.

- 리플로우는 비용이 큰 작업인데, 그 이유는 특정 요소에서 리플로우가 발생하면 주변 요소(부모,자식,형제)에도 영향을 주기 때문입니다.

<br/>

> **🤔 reflow 발생 시점은 언제에요?**
> a. DOM 요소의 크기,위치,구조 등 속성이 변경될 떄(width,height 등)
> b. 브라우저 사이즈가 변할 때
> c. 텍스트 내용, 이미지 등 컨텐츠가 동적으로 변경될 때
> d. JS DOM관련 메소드를 실행하거나 속성에 접근할 때

<br/>

## ✔️ 리페인트(repaint)

- 변경된 요소를 화면에 그려주는 작업을 리페인트 라고 합니다.
- 리페인트는 요소의 스타일이 변경되었을 때 발생하므로 **리플로우** 보다 비용이 적습니다.

> **🤔 리페인트 발생 시점은 언제에요 ?**

1. 리플로우가 발생했을 때
2. 요소의 스타일(색상,배경색 등)이 변경되었을 때
3. visibility 속성, opacity 속성이 변경될 때
4. 요소의 포커스가 변경될 때

> **🤔 visibility가 변경되는게 리페인트면 display:none 도 리페인트인가요 ?**

- visibility 는 화면에서 공간을 차지하면서 보이지 않는 반면 display:none 는 영역도 차지하지 않으면서 보이지 않게 합니다
- visibility : hidden 이 적용된 요소는 단순히 보이지 않을 뿐 크기나 위치가 변하는게 아니기에 리플로우는 발생하지 않고 리페인트만 발생합니다 -영역을 차지하지 않는다는 말을 곧 렌더트리에서 제외된다는 말이므로, display: none이 적용된 요소는 영역이 사라지면서 주변요소의 위치, 크기에도 영향을 주어 리플로우, 리페인트가 발생한다.

## 🤔 리플로우 줄이는 방법이 뭐가 있을까요 ?

- 애니메이션이 적용된 요소의 trasnform 과 opacity를 설정하여 리플로우 최소화
- 이벤트 핸들러 사용시 DOM을 조작하는 경우도 리플로우가 발생하니 이벤트를 효율적으로 처리
- JS 작업이 비동기적으로 처리되면 여러 작업을 한번에 처리할 수 있으므로 최소화
- CSS 클래스 스타일 변경하기

## 🤔 리페인트 줄이는 방법은 뭐가 있을까요 ?

- 가상 DOM 사용하기
- CSS 속성 사용 최적화 하기
- 이미지 및 그래픽 최적화 하기
- 성능 분석 도구를 사용하여 최적화 할 수 있는 부분 식별하기