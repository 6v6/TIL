# 생활코딩, 인프런 :: 지옥에서 온 Git
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

### 분석도구 gistory 소개
-   파이썬 설치
-   pip install gistory

### git add

-   git init : 초기화
-   gistory
    -   vim f1.txt : 파일 추가, 파일 추가에 대해선 변화 없음
    -   git add f1.txt : index, objects/78/98~~85 변화 두가지
        -   index : 파일의 이름은 index에. f1.txt에 대한 정보는 78/98~~85에 적혀 있다는 것을 알려줌
        -   objects : 파일의 내용은 objects에 담겨 있음 objects에 담겨 있는 파일들을 object(객체)라 부름
    -   git은 어떠한 파일을 저장할 때, 파일의 이름이 달라도 파일의 내용이 같으면 같은 object 파일을 갖는다
        -   ex) 만개의 파일이 각각 아무리 용량이커도 내용이 같으면인덱스에는 각각의 파일명만 적혀 있고 만개의 파일은 같은 object를 가리킴.

### objects 파일명의 원리
- 내용이 같으면 파일의 이름이 같은 메커니즘
- http://www.sha1-online.com/
- 입력어는 sha1이라는 hash메커니즘을 통과하면 도출 되는 값의 앞 두글자를 디렉토리 이름으로, 그 뒤에 내용으로 시작하는 파일에 저장.

    
### commit의 원리
- 방금 커밋한 결과는 objects파일로 저장이 되고 objects파일에는 tree라는 것이 적혀있음
- tree에는 우리가 작성한 파일의 이름과 내용이 링크되어있음
- 각각의 버전은 트리라는 정보구조를 통해 갖고 있음. 
- 첫번째 커밋과 두번째 커밋의 tree값이 다름 
- 커밋에는 부모를 나타내는 값, 커밋이 일어난 시점에 작업 디렉토리에 있는 파일의 이름과 파일의 이름이 담고 있는 내용 사이의 정보가 tree에 담겨있음
- 버전에 적혀있는 tree를 통해서 버전이 만들어진 시점의 프로젝트 폴더에 대한 상태를 알 수 있음. => snampShot이라 얘기함
- 각각의 버전은 만들어진 시점에 만들어진 스냅샷은을 트리라는 정보 구조를 통해 갖고 있음.
- objects 파일은 크게 세가지 형태
	- '파일의 내용을 탐고 있는 blob'
    - 디렉토리에 파일명과 파일명에 해당하는 내용에 해당하는 blob에 대한 정보를 담고 있는 'tree'
    - 'commit'

### status의 원리
> git status는 어떻게 내가 commit할 파일이 있는지 없는지 알 수 있을까?
	- 현재 최신 commit 두개 사이의 차이 비교! 
- working directory에서 add - index파일에 등록(staginf area) - commit - local repository에 저장 


## git의 혁신 - branch

## git의 원리

## 원격저장소

## 태그

## Rebase

## git을 이용한 프로젝트의 흐름

## git을 이용한 프로젝트의 흐름
