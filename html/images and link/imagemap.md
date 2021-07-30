# 이미지 맵 지정

## \<map>, \<area>

```html
<map name="맵이름">
    <area>
    <area>
</map>

<img src="이미지 파일" usemap="#맵이름">
```

## area 속성

### alt

대체 텍스트를 지정합니다.

### coords

링크로 사용할 영역을 시작 좌표와 끝 좌표를 이용해 지정합니다.

### download 

링크를 클릭했을 때 링크 문서를 다운로드한다.

### href

링크 문서(사이트) 경로를 지정합니다.

### media 

링크 문서(사이트)를 어떤 미디어에 최적화시킬지 지정합니다.

### rel

현재 문서와 링크 문서 사이의 관계를 지정합니다.

- 속성 값 : Iternate, bookmark, help, license, next, nofollow, noreferer, prefetch, prev, search, tag

### shape 

링크로 사용할 영역의 형태를 지정합니다.
-  속성 값 : defaul, rect, circle, poly

### target

링크를 표시할 대상을 지정합니다.
- 속성 값 : _blank, _parent, _self, _top, 프레임 이름

### type

링크 문서의 미디어 유형을 지정합니다.