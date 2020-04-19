#생활코딩, 인프런 :: 지옥에서 온 Git
> [인프런 : 지옥에서 온 Git](https://www.inflearn.com/course/%EC%A7%80%EC%98%A5%EC%97%90%EC%84%9C-%EC%98%A8-git/)

## 버전관리의 본질

### git init

### git add

-   cd 경로명 : 디렉토리 열기 (접근)
-   git status : 현재 git의 상태
-   ls - al : 현재 위치의 모든 파일 조회

### 버전만들기(commit)

-   계정 정보 설정
    -   git config --global user.name 닉네임
    -   git config --global user.enail 이메일
    -   \=> 닉네임과 이메일 정보를 포함하고 있는 버전이 되기 때문에 다른사람이 봤을때 누가 작업 했는지 알 수 있음.
-   버전 생성 방법
    1.  git add \[버전관리를 할 변경된 파일명\]
    2.  git commit -> vimd으로 들어가짐 -> i를 눌러서 안에 commit 메시지 작성 - esc - :wq
    3.  git log : commit이 됐는지 기록 확인

### git stage area

-   stage: 커밋 대기를 하고 있는 파일이 가는 곳
-   repository : 커밋한 결과가 저장 되는 곳

### 변경사항 확인하기(log&diff)

-   git log -p : 각각의 commit과 commit사이의 소스상의 차이를 확인 할 수 있음
-   git diff \[커밋메시지1\]..\[커밋메시지2\] : 커밋메시지1와 커밋메시지2 사이의 차이를 볼 수 있음
-   git diff : 현재 작업과 이전 작업의 차이를 볼 수 있음 -> 커밋 전에 작업한 내용의 리뷰 가능

### 과거로 돌아가기(reset)

-   commit을 취소하고 과거로 돌아가기
-   git reset \[커밋 주소\] --hard : 커밋 주소로 초기화 됨 (이후의 커밋이 보이지 않음)
-   git revert : 커밋을 취소하면서 새로운 버전 생성

### 스스로 공부하는 법

-   메뉴얼을 보기, 커밋메시지 확인하기, 검색하기
-   git commit --help : commit message에 대한 옵션, 메뉴얼을 볼 수 있음
-   git commit \[-a/--al\] : 수정하거나 삭제한 파일을 자동으로 stage에 올린다
-   git commit \[-m 'msg'\] : msg를 커밋메시지로 사용한다
-   git commiat -am "11" : 에디터를 키지 않고 커밋할 수 있음, '수정한 파일을 '11'을 커밋메시지로 커밋함'

## git의 원리

## git의 혁신 - branch

## git의 원리

## 원격저장소

## 태그

## Rebase

## git을 이용한 프로젝트의 흐름