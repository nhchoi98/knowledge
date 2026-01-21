# CSS

# 기본

## 선택자

CSS에서는 스타일 속성을 적용하는 요소들을 선택자라고 합니다. CSS 문법에서는 가장 앞에 나오는 대상이 되는 타겟을 의미하며 이를 통해 스타일을 적용할 수 있게 됩니다. 이 선택자는 태그의 전체가 될 수도 있고, 때로는 여러 개의 요소들을 묶어 별도의 선택자로 만들 수도 있습니다. 

## Flex - Container

### Flex box

 flexbox 인터페이스 내의 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델 로 설계되었습니다. 이 글에서는 flexbox의 주요 기능에 대한 개요를 다룹니다. 더 자세한 내용은 가이드의 다른 글에서 탐구하게 될 것입니다.

flexbox를 1차원이라 칭하는 것은, 레이아웃을 다룰 때 한 번에 하나의 차원(행이나 열)만을 다룬다는 뜻입니다. 이는 행과 열을 함께 조절하는 [CSS 그리드 레이아웃](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_grid_layout)의 2차원 모델과는 대조됩니다.

flexbox를 다루려면 주축과 교차축이라는 두 개의 축에 대한 정의를 알아야 합니다. 주축은 [`flex-direction`](https://developer.mozilla.org/ko/docs/Web/CSS/flex-direction) 속성을 사용하여 지정하며 교차축은 이에 수직인 축으로 결정됩니다. flexbox의 동작은 결국 이 두 개의 축에 대한 문제로 환원되기 때문에 이들이 어떻게 동작하는지 처음부터 이해하는 것이 중요합니다.

### Flex?

하나의 플렉스 아이템이 자신의 컨테이너가 차지하는 공간에 맞추기 위해 크기를 키우거나 줄이는 방법을 설정하는 속성입니다. 

### Content

::before와 ::after 가상 요소에 콘텐츠를 삽입하기 위한 속성공백(space)으로 구분하여 여러 가지 값을 삽입할 수 있다.

- ::before와 ::after 가상 요소에 콘텐츠를 삽입하기 위한 속성
- 공백(space)으로 구분하여 여러 가지 값을 삽입할 수 있다.

### Padding

 [CSS](https://developer.mozilla.org/ko/docs/Web/CSS) 속성은 요소의 네 방향 [안쪽 여백 영역](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model#padding-area)을 설정합니다. [`padding-top`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-top), [`padding-right`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-right), [`padding-bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-bottom), [`padding-left`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-left)의 단축 속성입니다.

### Border

### Margin

### Box sizing

CSS 박스 모델의 기본값에서, 지정한 너비와 높이는 요소의 콘텐츠 박스 크기에만 적용됩니다. 요소에 테두리나 안쪽 여백이 있으면 너비와 높이에 더해서 화면에 그립니다. 따라서 크기를 설정할 때, 원하는 크기를 얻으려면 테두리나 안쪽 여백을 고려해야 합니다.

`box-sizing` 속성을 사용해 이 방식을 바꿀 수 있습니다.

- `content-box`는 기본 CSS 박스 크기 결정법을 사용합니다. 요소의 너비를 100 픽셀로 설정하면 콘텐츠 영역이 100 픽셀 너비를 가지고, 테두리와 안쪽 여백은 이에 더해집니다.
- `border-box`는 테두리와 안쪽 여백의 크기도 요소의 크기로 고려합니다. 너비를 100 픽셀로 설정하고 테두리와 안쪽 여백을 추가하면, 콘텐츠 영역이 줄어들어 총 너비 100 픽셀을 유지합니다. 대부분의 경우 이 편이 크기를 조절할 때 쉽습니다.

- **정상 흐름 & 포맷팅 컨텍스트**: 블록/인라인 흐름, **BFC**(overflow/float 등으로 생성), 레이아웃 붕괴 방지.
- **캐스케이딩/상속**: **특이도(specificity)**, 선언 순서, 상속 규칙.
    - `:where()`(특이도 0), `:is()`(가장 강한 선택자 상속), `@layer`(레이어별 우선순위) 이해.
- **선택자**: 기본/속성/nth-*/조합자, **:hover / :focus-visible / :focus-within / :has()**.
- **단위**: `px`, `%`, `em/rem`, `vw/vh`, `svh/dvh`, `ch`, `min()/max()/clamp()`, `calc()`.
- **색/투명도**: `hsl()`, `rgba()`, (여유되면 `oklch()` 개념도).
- **표시/위치**: `display`(block/inline/inline-block/contents), `position`(static/relative/absolute/fixed/**sticky**),
    
    **쌓임 맥락( stacking context )**과 `z-index`, `transform`이 새 쌓임 맥락 만드는 것.
    

## 표시(Display)

### Block

웹페이지의 **블록**은 HTML 요소로 새 줄에 표시됩니다. 즉, 가로 쓰기 모드에 속한 선행 요소 아래나 ("블록 수준 요소"로 통용되는) 후속 요소 위에 표시됩니다. 예를 들면, `p`는 기본적으로 블록 수준 요소지만, `a`는 "인라인 요소"이다. 당신의 HTML 소스에서 여러 링크를 상대 요소 옆에 위치시킬 수 있고, 그것들을 렌더링 된 출력 형태로 상대 요소와 동일 선상에 놓는다.

### Inline

전후 줄바꿈 없이 한 줄에 다른 엘리먼트들과 나란히 배치됩니다. 대표적인 `inline` 엘리먼트로 `<span>`이나 `<a>`, `<em>` 태그 등을 들 수 있습니다.

### Inline-block

Block 처럼 요소의 앞뒤를 줄바꿈 시키는 특징은 없지만, 너비([`width`](https://codingeverybody.kr/css-width-%ec%86%8d%ec%84%b1/))와 높이([`height`](https://codingeverybody.kr/css-height-%ec%86%8d%ec%84%b1/)) 같은 컨테이너 영역을 정의할 수 없는 [`display: inline`](https://codingeverybody.kr/css-display-inline/)과는 다르게 [`display: block`](https://codingeverybody.kr/css-display-block/)처럼 컨테이너 영역을 정의할 수 있습니다.

### Contents

`display: contents`는 **요소 자신은 박스를 만들지 않고, 자식들만 부모의 직계 자식처럼 레이아웃에 참여**하게 만드는 값이에요. 즉, DOM에 그룹용 래퍼를 남겨두면서 시각적으로는 그 래퍼를 “투명”하게 만드는 느낌입니다.

- ✅ 래퍼를 시각적으로 없애고 자식들을 한 단계 끌어올리고 싶을 때 유용
- ❌ 박스 기반 스타일(배경/여백/보더/포지션 등)을 그 요소에 주어도 **효과 없음**
- ⚠️ `<img>`, `<input>` 등 **대체 요소엔 쓰면 안 됨**(사실상 숨김)
- ⚠️ **접근성 이슈** 가능: 시맨틱/ARIA 래퍼에 적용 시 보조기기 테스트 필수
- ⚠️ **컨테이너 쿼리 컨테이너**로 쓰고 싶다면 `display: contents` 사용 금지

## Cascading / Override

여러 CSS 규칙이 한 요소를 두고 서로 충돌할 때 **최종값 하나**를 고르는 공식”이에요.

쉽게 말해 **적용 가능한 규칙들 → 우선순위 비교 → 동률이면 무승부 규칙** 순서로 챔피언을 뽑는 과정입니다.

### 한 줄 공식

적용됨(조건 만족) → **중요도/출처** → **레이어(@layer)** → **특이도** → **선언 순서(나중 것이 이김)**

- **Transition**이 만든 값 (가장 셈)
- `!important` 있는 규칙
    - **사용자 스타일(유저)** `!important`
    - **작성자(Author)** `!important` ← 우리가 쓰는 일반 CSS의 `!important`
- **Animation**이 만든 값
- `!important` 없는 규칙
    - 작성자(Author) 일반 규칙
    - 사용자(User) 일반 규칙
    - 브라우저 기본(UA) 규칙

`@layer base, components, utilities;`처럼 **레이어 순서**를 선언해 두면,

**서로 다른 레이어끼리는 특이도와 무관하게 레이어 순서가 먼저** 비교됩니다.

- 레이어 순서는 **처음 선언한 순서**로 고정됩니다(나중에 같은 레이어에 추가해도 순서는 그대로).
- 서로 다른 레이어끼리 충돌하면 **뒤쪽 레이어가 이김**.
- **같은 레이어 안**에서는 다음 단계(특이도→선언순서)로 넘어갑니다.

### 4) 특이도(Specificity)

선택자 힘 대결입니다. 대략:

- 인라인 스타일 `style=""` > ID 선택자(`#id`) > 클래스/속성/가상클래스(`.class`, `[type]`, `:hover`) > 태그/가상요소(`h1`, `::before`)
- `:where()`는 **특이도 0** (우선순위 올리지 않고 스타일만 묶고 싶을 때 유용)
- `:is()`는 괄호 안 **가장 강한 선택자**의 특이도를 가짐

### 5) 선언 순서(Source order)

위가 다 같으면 **나중에 나온 규칙이 승리**합니다(같은 파일/레이어/특이도 기준).

## Stacking context

# 2) 현대 레이아웃 핵심

- **Flexbox**: 1차원 정렬(가로/세로), **정렬 축**(main/cross), `gap`, `flex: 1`과 **`min-width: 0` 함정**(오버플로 방지).
- **Grid**: 2차원, `repeat()`, `minmax()`, `auto-fit/fill`, 콘텐츠 기반 크기(`min-content/max-content`),
    
    필요하면 **subgrid** 개념까지.
    
- **정렬 패턴**: 가운데 정렬 → `place-items: center`(grid), `justify/align` 조합(flex).
- **비율 유지**: `aspect-ratio`로 카드/썸네일 안정화.
- **간격**: 가능하면 `gap` 우선(마진 대신).

# 3) 반응형 & 적응형

- **미디어쿼리**: `@media (width >= 768px)` 스타일(범위 구문), 포인터/호버/명암 등 환경쿼리.
- **컨테이너 쿼리**(필수 트렌드): 컴포넌트가 **부모 너비**에 반응.
    
    ```css
    .card { container-type: inline-size; }
    @container (min-width: 480px) { .title { font-size: 1.25rem; } }
    
    ```
    
- **유동 타이포**: `clamp(1rem, 2vw + .5rem, 1.5rem)` 같은 패턴.
- **뷰포트 이슈**: 모바일은 `svh/dvh`로 주소창 변화 대응.

# 4) 타이포그래피 & 미디어

- **라인 높이**: 단위 없는 `line-height: 1.5;` 권장(상속 안정).
- **가독성**: `letter-spacing`, `word-break/overflow-wrap`, `hyphens`.
- **폰트**: `@font-face`, `font-display: swap`, **가변 폰트**(축 조절).
- **이미지/비디오**: `object-fit/position`, `aspect-ratio`, 반응형 이미지(HTML `srcset/sizes`) 개념.

# 5) 상호작용/애니메이션

- **전환/애니메이션 성능**: **`transform`/`opacity`** 위주, `top/left` 이동 지양.
- **접근성 고려**: `@media (prefers-reduced-motion: reduce)` 분기.
- **상태 스타일**: `:focus-visible`로 키보드 포커스 보장, `:has()`로 부모-자식 상태 연동.

# 6) 구조/아키텍처

- **리셋/프리플라이트**: 기본 UA 스타일 상쇄, `{ box-sizing: border-box }`.
- **토큰/변수**: CSS 커스텀 프로퍼티(`-color-primary`), 다크모드/테마 전환.
- **레이어링**: `@layer base, components, utilities;` → 충돌 줄이기.
- **네이밍/스코프**: BEM, 모듈(CSS Modules), CSS-in-JS, Shadow DOM(`:host`, `::part`, `::slotted`) 이해.

# 7) 접근성 기본

- 포커스 가시성(`:focus-visible`), **명도 대비**(텍스트/아이콘), **히트 영역**(터치 크기),
    
    `cursor` 남용 금지, 콘텐츠 순서와 시각 순서 일치, `prefers-contrast` 인지.
    

# 8) 디버깅 & 성능

- **DevTools**: 레이아웃/그리드/플렉스 오버레이, **Box Model** 탭, 강제 상태(:hover 등), 애니메이션 패널.
- **성능**: 크리티컬 CSS, 폰트 지연 최소화(`preload`, `font-display`), 거대/깊은 그림자/블러 남용 주의.
- **호환성/프로그레시브**: `@supports`로 기능 감싸기, 점진적 향상.

## Flex-basis

**`flex-basis`** [CSS](https://developer.mozilla.org/ko/docs/Web/CSS) 속성은 플렉스 아이템의 초기 크기를 지정합니다. [`box-sizing`](https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing)을 따로 지정하지 않는다면 콘텐츠 박스의 크기를 변경합니다.

## Cascading 규칙 정리 (우선순위)

1. **출처**: 개발자 `!important` > 사용자 `!important` > 개발자 CSS > 사용자 CSS > 브라우저 기본 CSS
2. **명시도**: 인라인 > ID > 클래스/속성/가상클래스 > 태그/가상요소
3. **선언 순서**: 같은 조건이면 나중에 작성된 것이 적용

## 

[SCSS](CSS/SCSS%2026ccee38e89a808bb01fd62a41ff92ab.md)