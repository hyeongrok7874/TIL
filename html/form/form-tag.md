# \<form>

## 용도

> 폼을 만드는 가장 기본적인 태그

## 속성

### method

사용자가 입력한 내용들을 서버 쪽 프로그램으로 어떻게 넘겨줄지 지정합니다.<br>
> get - 주소 표시줄에 사용자가 입력한 내용이 그대로 드러난다.<br>
> post - 대부분 이 방식을 사용한다. 사용자가 입력한 내용이 드러나지 않습니다.

### name

폼의 이름을 지정합니다. 한 문서 안에 여러 개의 \<form> 태그가 있을 경우, 폼들을 구분하기 위해 사용합니다.

### action

\<form> 태그 안의 내용들을 처리해 줄 서버 상의 프로그램을 지정합니다.

### target

action 속성에서 지정한 스크립트 파일을 현재 창이 아닌 다른 위치에 열도록 지정

## 종류

### \<select>, \<option>, \<optgroup>

옵션 중에 선택하도록 할 때 사용

```html
<select>
    <optgroup>
        <option>내용</option>
        <option>내용</option>
    </optgroup>
    <optgroup>
        <option>내용</option>
        <option>내용</option>
    </optgroup>
</select>
```

### \<datalist>, \<option>

텍스트 필드에 직접 값을 입력하는 것이 아니라 데이터 목록에 제시한 값 중에서 선택하면 그 값이 자동으로 입력된다.

### \<textarea>

여러 줄 입력하는 텍스트 영역 만든다.

### \<button>

폼을 전송하거나 리셋하기 위한 버튼 삽입
- submit : 폼을 서버로 전송한다.<br>
- reset : 폼에 입력한 모든 내용을 초기화시킵니다.<br>
- button : 버튼 형태만 만들 뿐 자체 기능은 없습니다.

### \<output>

입력하는 값이 계산 결과라는 것을 브라우저에게 알려준다.

### \<progress>

진행 상태 보여주기 

### \<meter>

값이 차지하는 크기 표시하기