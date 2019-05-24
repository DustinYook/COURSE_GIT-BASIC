GIT2 강의내용 정리

# 버전관리
- **CLI의 장점** : 처리업무의 자동화, 서버환경 사용가능, 파일명 건들지 않고 변경사항 해설추가
- **터미널, 콘솔** : 명령어를 입력가능한 검정색 창
- **버전관리 명령어**
	- **mkdir** hello-git-cli : 디렉터리 생성
	- **cd** hello-git-cli : 생성한 디렉터리로 이동
	- **ls -al** : 모든 파일, 디렉터리의 목록 보여줌
	- **git init .** : 현재 디렉터리를 깃에게 버전관리 시킴
	- **.git** : 깃의 모든 히스토리, 버전정보 관리정보 저장

-----

### 1. Git의 동작원리
- **working tree** : 수정한 파일 있는 곳
- **staging area** : 버전이 될 파일 있는 곳
- **repository** : 버전이 저장되어있는 곳
 
	#### 1) working tree
	- **touch** a.txt : 파일을 생성 **(untracked)**
	- **cat** a.txt : 내용 화면 출력
	- **git status** : working tree의 변경사항 확인
	
	#### 2) working tree -> staging area
	- **git add** a.txt : 버전관리할 거고 **staging area**로 옮겨줘! **(tracked)**
	- changes to be committed : 버전 될 파일목록
	- 참고) commit은 버전과 같은 말이다!
	 
	#### 3) staging area -> repository
	- **git commit -m "메모내용"** : 버전생성 및 **repository로 이동**시킴
	- **git log** : commit history 확인 시 사용

-----
	
### 2. 여러 파일을 하나의 버전으로 관리
- **tracked** : 협업 또는 백업하고자 하는 파일
- **untracked** : 협업 또는 백업 원치 않는 파일
- **버전 관리를 위한 명령어**
	- **git add** 대상파일 : staging area로 올림 **(tracked)**
	- (changes to be committed : staging area에 존재)
	- **git commit -m "메모내용"** : repository로 올림
	- **git log** : 지금까지의 commit history 표시
	- **git log --stat** : 관련파일, 변경사항 표시
- 여러 개의 파일을 그룹핑하여 관리할 수 있음

-----

### 3. Git의 유용한 기능
- **git diff** : working tree와 직전 버전과 차이점 표시
	- '+' : 새로 추가된 것
	- '-' : 삭제된 것
	- 장점 : 새로운 버전 제출하기 전에 다시 검토 가능
- **git reset --hard** : 작성한 것을 기존상태로 롤백함
- **git log -p** : 모든 변경사항을 파악가능 (patch)

-----

### 4. 특정시점의 버전으로 이동
- **master** : 최신버전
- **HEAD** : 지금 어떤시점의 버전인지 가리키는 포인터 - ex) HEAD -> master : 최신버전 가리킴
- **특정시점의 버전으로 이동하는 방법**
	1) git log 입력
	2) commit 버전명 : 각 시점의 버전이름 파악가능
	3) git checkout 버전명 : 해당 시점으로 이동 (HEAD -> 버전명으로 변경됨)
	4) git checkout master : 최신버전으로 이동

-----

### 모르면 풀편한 Git 명령어
- **git add .** : 현재 디렉토리의 모든 파일 add
- **git add 디렉터리명** : 지정 디렉토리 모든 파일 add
- **git commit -am "메모"** : add, commit 동시처리
	- 주의) untracked 상태인 것은 처리하지 못함, 최소 한번은 git add를 해준 후 -am을 써야함
- **git commit -m "메모"** : CLI에서 한 줄 메모 입력
- **git commit** : 기본 에디터에서 여러 줄 메모 입력
- **git config --global core.editor "vim"** : 디폴트 에디터를 vim 에디터로 설정

-----

### 버전 삭제방법
- **git reset --hard 버전명** : 해당 버전이 되겠다
	- 주의) 해당 버전 삭제가 아닌 해당 버전으로 리셋
	- --hard : working tree의 현재작업과 해당버전 지움
	- --로 시작하는 것은 mode라 함
- 다른 사람과 공유된 버전은 리셋하면 엉키는 문제발생 (공유되기 전 단계의 버전만 리셋해야 됨)

-----

### 버전 되돌리기
- CRUD에서 UD는 엄격히 통제하는 경우 존재
- 삭제의 목적과 보존의 목적을 동시에 달성
- **주의) reset과 revert는 대상이 다름**
	- ver1 ver2 ver3 ver4 (HEAD -> ver4)
	- **git reset --hard ver3** : ver3로 리셋
	- **git revert ver4** : ver4에서 ver3로 리버트
	- 기본 에디터가 뜨면 왜 리버트하는지 메모 남김
- **주의) 만약 ver2로 리버트하고 싶다면?**
	- git revert ver3로 하면 충돌 발생함
	- 반드시 git revert ver4, git revert ver3를 순서대로 해줘야 충돌없이 리버트를 할 수 있다
	- 즉, 해당 버전에 이르기까지 역순으로 리버트 수행
	- conflict(충돌) : 깃이 정보유실 등 문제로 컴플레인

-----

### 강의를 마무리하며
- 버전관리의 핵심은 **비교** : 비교를 통해 과거를 되돌아 볼 수 있음
- **diff tool**을 통해 정교하게 차이점 파악할 수도 있음
- **.gitignore** : 버전관리를 하지 말아야 할 파일목록
	- 예시) 민감파일, 임시파일 등
- **branch** : 저장소를 여러상태로 공존하게 해줌
- **tag** : 복잡한 commit ID 대신 이름을 붙일 수 있음