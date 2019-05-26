# GIT3 - CLI Branch & 충돌

- [참고] <https://opentutorials.org/module/3927>
- 아래 요약본은 이고잉님의 위 강의를 기반으로 작성되었습니다. 

### 1. 기본 용어정리
- **branch** : 같은 뿌리에서 나왔지만 서로 다른 역사를 쓰고 있는 버전들
	- 다른 파일 수정 후 병합 : 문제 없음
	- 같은 파일 다른 위치 수정 후 병합 : 문제 없음
	- 같은 파일 같은 위치 수정 후 병합 : 병합중지, 충돌
- **conflict** : 수동으로 처리하라고 알려주는 역할 (같은 파일, 같은 부분 병합)
- **HEAD** : **현재 속해있는 브랜치**를 나타내는 포인터 - ex) HEAD -> master : 현재 master에 있음
- **master** : 저장소 생성 시 디폴트 브랜치
![jargon](https://github.com/DustinYook/Course_Git/blob/master/image/jargon.jpg)
- **base** : merge하고자 하는 두 브랜치의 **공통조상**
- **merge commit** : 두 브랜치를 **merge한 결과** 브랜치
- **commit ID** : 버전의 이름
- **checkout** : **HEAD의 값을 바꾸는 것** (HEAD는 브랜치 또는 버전을 가리킬 수 있다)
- **detached** : HEAD가 브랜치가 아닌 **버전을 가리키는 상태**

### 2. 명령어 정리
- **git log -p** : 각 **버전별 차이**를 쉽게 파악가능
- **git log --all** : 생성된 **모든** 브랜치 로그
- **git log --graph** : 시각적으로 로그가 표현
- **git log --oneline** : 버전이 한 줄로 나옴
- **git branch** : 현재 **존재하는 브랜치**를 보여줌
- **git branch 브랜치명** : **브랜치 생성** (브랜치 이동은 X)
- **git checkout 브랜치명** : **브랜치를 전환**, 브랜치의 마지막 커밋상태로 working copy가 바뀜
	- 장점 : 공통작업을 공유하며 별도의 작업을 진행가능 - ex) 고객별 효율적 프로젝트 관리가능
- **git commit --amend** : 이미 commit한 것의 메모 수정가능
- **git init 디렉터리명** : 디렉터리 생성 및 초기화 동시에

### 3. 병합과정 정리
- **A브랜치를 B브랜치에 병합하고자 함**
	1) B브랜치로 checkout (해당 브랜치로 간다)
	2) git merge A (다른 브랜치 내용을 땡겨온다)
- **병합을 취소하고자 함**
	- **git reset --hard <병합 전 B의 버전>** 


### 4. 충돌해결과정 정리

- **같은 파일, 같은 부분 병합 시 아래와 같이 나옴**

**1) conflict 발생 상황**

	 <<<<< HEAD // master
	 master // master
	 ======= // 구분자
	 o2 // o2
	 >>>>> o2 // o2

**2) conflict 해결** : <<<와 >>> 지우고 코드 정리

	 master, o2

### 5. 3-way-merge
1) **2-way-merge** 
	- 두 브랜치를 비교해서 merge
	- 같으면 그대로, 다르면 충돌발생

2) **3-way-merge** : 두 브랜치와 공통조상 base를 비교
	- 바뀌지 않은 경우 : base 그대로
	- 한 브랜치만 바뀐 경우 : 수정된 브랜치 내용 따름
	- 두 브랜치 모두 바뀐 경우 : conflict 발생시킴
	- 훨씬 더 많은 부분을 자동화하여 병합이 가능


### 6. 수업을 마치며
- **p4Merge** 
	- diff는 차이점 비교, merge는 차이점 비교와 병합 동시에 수행
	- [다운로드 받을 수 있는 URL](https://www.perforce.com/downloads/visual-merge-tool)
	- [p4Merge를 windows OS에서 Git에 설정하는 방법](https://gist.github.com/dgoguerra/8258007)
	- **git config --global merge.tool p4mergetool** : 기본 merge tool을 p4Merge로 설정하는 방법
	- 설정 후 git mergetool 명령어 입력
		- **local** : 내가 현재 있는 브랜치
		- **remote** : 내가 당겨오려는 브랜치
- **git workflow** 검색 
	- **git flow** : 일종의 모범사례, 표준따르며 업무집중 
	- **cherry-pick** : 병합과 관련, 부분병합 가능
	- **rebase** : merge와 목표는 같음, 타임라인 깔끔해짐
- **checkout vs reset**
	- checkout은 언제나 HEAD를 제어한다
	- reset은 HEAD가 브랜치를 가리키는 동안에는 브랜치를 제어한다
- **checkout master vs reset master**
![diff](https://github.com/DustinYook/Course_Git/blob/master/image/diff.jpg)
	- checkout은 change의 의미 
	- reset은 delete의 느낌
	- 주로 reset뒤에는 브랜치가 아닌 버전이름이 옴
	
