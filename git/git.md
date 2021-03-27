# git

## git 이란?
> 깃(Git /ɡɪt/)은 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템이다.

## git 용어
> 작업 트리 : 파일 수정, 저장 등의 작업을 하는 디렉터리<br>
> 스테이지 : 버전으로 만들 파일이 대기하는 곳<br>
> 저장소 : 스테이지에서 대기하고 있던 파일들을 버전들로 만들어 저장하는 곳<br>

## git 명령어
> git add : 스테이징<br>
> git add . : 수정된 파일을 한꺼번에 스테이지에 올릴 수 있다<br>
> git commit -m : 커밋 메시지와 함께 커밋<br>
> git commit -am : 스테이징과 커밋 한번에 처리. 한 번이라도 커밋한 적이 있는 파일을 다시 커밋<br>
> 
> git diff : 변경 사항을 확인<br>
> git log : 저장소에 저장된 버전 확인<br>
> git log --stat : 커밋에 관련된 파일까지 함께 살펴보기 <br>
> (q로 로그 화면을 빠져 나올 수 있다)<br>
> git status : 깃 상태 확인<br>
>> In branch master : 현재 master 브랜치에 있다<br>
>> No commits yet : 아직 커밋한 파일이 없다<br>
>> nothing to commit : 현재 커밋할 파일이 없다<br>

## git 취소 명령어
> git checkout -- 파일이름 : 변경 사항 취소<br>
> git reset HEAD 파일이름 : 스테이지에서 내림<br>
> git reset HEAD^ : 가장 마지막의 커밋을 취소한다<br>
> git reset —soft HEAD^ : 최근 커밋을 하기 전 상태로 작업 트리를 되돌린다<br>
> git reset —mixed HEAD^ : 최근 커밋과 스테이징을 하기 전 상태로 작업 트리를 되돌린다. 옵션 없이 git reset 사용시 이 옵션이 기본<br>
> git reset —hard HEAD^ : 최근 커밋과 스테이징, 파일 수정을 하기 전 상태로 작업 트리를 되돌린다. 복구 불가능<br>
> git reset 커밋 해시 : 커밋 해시로 되돌아감<br>
> git revert  커밋 해시 : 커밋 해시 전 버전으로 새 커밋을 만듬 (커밋 해시 버전이 남아 있다)

## git 상태
> tracked 상태 : 깃이 추적하고 있는 파일(한 번이라도 커밋한 파일)<br>
> untracked 상태 : 깃이 추적하고 있지 않는 파일(한 번도 버전 관리를 하지 않은 파일)<br>
> modified 상태 : 수정된 상태<br>
> unmodified 상태 : 수정되지 않은 상태<br>
> staged 상태 :  커밋 직전 단계