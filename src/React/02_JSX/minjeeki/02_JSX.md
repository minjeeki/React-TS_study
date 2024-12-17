# 02_JSX

## JSX (JavaScript Extensions)

: 확장된 자바스크립트 문법 (일종의 자바스크립트 확장판)

> 자바스크립트 문법은 return문 안에 html 태그를 명시할 경우 오류라고 판단한다
하지만 리액트에서는 JSX라는 확장된 자바스크립트 문법을 사용하기 때문에 적법하다고 판단한다
> 
- 자바스크립트와 html을 혼용해서 사용할 수 있도록 해준다
- 함수 컴포넌트 내부 변수가 html 태그 내부로 렌더링할 수 있도록 해준다
(동적으로 특정 변수의 값을 html로 렌더링할 수 있도록 해준다)
    - HTML 태그 내부에 중괄호를 사용해서 값 또는 변수를 지정해서 사용한다
    - 중괄호 내부의 값은 숫자나 문자열의 값으로 평가될 수 있는 식이 들어갈 수 있다
    - 중괄호 내부에는 html 태그가 들어갈 수도 있다
    (ex. 삼항연산자 사용해 로그인 여부에 따라 다른 버튼 사용)

### JSX 사용 주의사항

- 중괄호 내부에는 자바스크립트 표현식만을 넣을 수 있다
    - 자바스크립트 표현식 : 삼항 연산자, 값, 변수 / 한줄의 코드가 값으로 평가될 수 있는 식
    - if문, for문 등은 사용할 수 없음 (함수 컴포넌트 내부에서 사용할 것)
- JSX에서는 숫자가 문자열, 배열의 값만 정상적으로 렌더링된다
    - boolean, undefined, null 등은 사용할 수 없다
    - 객체 자체를 렌더링할 경우 `Object are not valid as a React child` 과 같은 오류 발생
    점 표기법을 통해 문자나 숫자의 값을 렌더링하도록 바꿔줘야 한다
- 모든 태그는 닫혀있어야 한다
    - <img>와 같은 빈태그의 경우에도 오류가 발생할 수 있다
        
        ⇒ <img/>와 같이 셀프 클로징 or <img></img>의 형태로 명시한다
        
- return값으로 인식되는 최상위 태그는 반드시 하나여야 한다
    - 마땅히 감쌀 태그가 없을 경우 `<> </>` 내부에 태그를 작성해 빈태그의 형태로라도 맞춰야 한다
    (JSX는 최상위 태그가 있다고 인식하나 실제 렌더링될 때는 반영되지 않음)

### JSX 스타일 설정 방법

1. 요소에 직접 스타일 지정하기 (인라인 스타일)
    - html 태그 내부에 style 속성 지정 + style 값은 중괄호를 두개 겹쳐서 사용
        
        `<div style={{ backgroundColor: "red" }}>`
        
    - 주의 사항 : 기존 css에서는 - 기호를 이용해 단어 구분을 했으나, 카멜케이스 사용
    - 방식의 단점 : 스타일이 많아질수록 가독성이 떨어짐
2. 별도의 CSS 파일을 만들어서 스타일 지정하기
    - jsx 파일 최상단에 css 파일 import (경로만 지정해줘도 리액트에서 알아서 css 파일 가져옴)
    - JSX에서는 HTML 문법을 같이 사용하고 있기 때문에
    `class` 라는 속성 대신 `className`이라는 속성을 사용해야 한다