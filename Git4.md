# GIT4 - CLI 협업

- [참고] <https://opentutorials.org/module/3967>
- 아래 요약본은 이고잉님의 위 강의를 기반으로 작성되었습니다. 

### 1. 로컬저장소에서 작업하는 방법
- git push **-u** origin master : 지역저장소와 원격저장소의 master가 pairing (한 번만!)
- **git clone 원격저장소URL 디렉터리명** : 디렉터리에 원격저장소의 내용을 복제
- **cp 디렉터리명** : 복사

### 1. 협업을 위한 원격저장소 설정방법 
- **오픈소스에서는 pull을 자유롭게 할 수 있지만 push를 하기 위해서는 설정이 필요하다**
	1) settings - collaborators & teams
    2) collaborators에 동료의 Github ID를 입력
    3) 동료에 자동으로 이메일 전송
    4) 동료가 이메일을 열고 accept (협업가능 상태)
	5) 동료에게 권한부여 가능 : admin/write/read (보통 write)
- 반드시 pull을 먼저하고 작업해야 한다
- 순서 : **pull - add - commit - push**
- 활발한 commit과 push를 통해 커뮤니케이션 촉진하는 자세가 필요


### 2. git pull = git fetch + git merge FETCH_HEAD
1) **pull** - add - commit - push
2) **fetch - mege FETCH_HEAD** - add - commit - push
	- **git fetch** : 원격저장소의 브랜치만 가져옴, 신중하게 Git의 데이터를 가져오고 싶을 때 사용
- **master** : **지역저장소**의 master 브랜치
- **origin/master** : origin이라는 **원격저장소**의 master 브랜치 (remote branch)
 
 
### 3. git patch
- **patch** : 정식 멤버가 아닌 사람이 참여할 수 있게 해줌
- patch 파일을 통해 변경사항 적용하는 방법
	- **git format-patch 버전이름** : patch 파일 생성
	- **git am -3 -i *.patch** : patch 파일을 적용


### 4. pull request
- **pull request** : 내가 변경한 것을 가져가달라 요청
- 오픈소스 : 누구나 pull할 수 있지만 아무나 push할 수는 없다
- **fork** : 원격저장소를 내 계정으로 복제하여 작업
- **clone** : 그 저장소에서 작업
- **pull request의 단계**
	1. compare : pull reqeust 전단계, 차이점 비교
	2. pull request : 원래 주인에게 내용반영해달라 요청
	3. confirm merge : request를 수락하고 merge


### 5. 강의를 마치며
- code review 도구 - Gerrit : push하면 투표소로 가서 동료투표거침
- issue tracker : 일종의 게시판 같은 기능
- 버전을 만들면서 파일의 이름을 더럽히지 않을 수 있다
- 협업을 하는 이유는 쉽기 때문이 아닌 가치있기 때문이다.
- Git은 여러개의 저장소를 연결시켜 상호간에 동기화