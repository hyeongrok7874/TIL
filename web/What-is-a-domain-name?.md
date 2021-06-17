# 도메인 네임이란?

## IP

> 컴퓨터 네트워크에서 장치들이 서로를 인식하고 통신을 하기 위해서 사용하는 특수한 번호이다.<br>
> 컴퓨터는 이러한 주소를 쉽게 처리 할 수 ​​있지만 사람들은 서버를 운영하는 사람이나 웹 사이트에서 제공하는 서비스를 찾는 데 어려움을 겪는다

## 도메인 네임

> 위의 문제를 해결하기 위해 도메인 이름이라는 사람이 읽을 수있는 주소를 사용한다.

## 도메인 이름의 구조

![도메인 구조](../img/structure.png)

### TLD

> 사용자에게 도메인 이름 뒤에있는 서비스의 일반적인 목적을 알려줍니다.

### lable

> 한 글자에서 전체 문장까지 무엇이든 될 수 있습니다. TLD 바로 앞에있는 레이블은 SLD 라고도 합니다.

## 도메인 네임 구매

> 도메인 네임은 구매가 아닌 임대할 수 있다

## DNS 요청

1. 브라우저의 위치 표시줄에 도메인 네임 입력
2. 브라우저는이 도메인 이름으로 식별 된 IP 주소를 이미 인식하는지 (로컬 DNS 캐시 사용) 컴퓨터에 묻습니다. 그렇다면 이름이 IP 주소로 변환되고 브라우저는 웹 서버와 콘텐츠를 협상합니다. 끝
3. 컴퓨터가 도메인 이름 뒤에 어떤 IP가 있는지 알지 못하는 경우 DNS 서버를 요청합니다. 그 역할은 정확히 어떤 IP 주소가 등록 된 각 도메인 이름과 일치하는지 컴퓨터에 알려주는 것입니다.
4. 이제 컴퓨터가 요청 된 IP 주소를 알고 있으므로 브라우저는 웹 서버와 콘텐츠를 협상 할 수 있습니다.