GIT3 강의내용 정리

# Git과 백업
- 컴퓨터는 언제 고장날지 확실치 않지만 반드시 고장
- **.git** : 버전정보를 저장하는 디렉터리
- **host** : 인터넷에 연결된 컴퓨터 한 대, 한 대
- **hosting** : 인터넷 연결된 서버를 임대해주는 서비스
- **git hosting** : local repository를 remote에 저장

### 1. 용어정리
- 백업을 위해서는 컴퓨터가 최소 2대 필요
- **local repository** : 작업을 해서 버전생성하는 컴퓨터에 있는 저장소 (내 컴퓨터)
- **remote repository** : 지역 저장소와 동일한 상태를 유지하는 컴퓨터에 있는 저장소 (Github)
- local repository -**PUSH**-> remote repository
	- 작업종료마다 push 통해 같은 상태로 유지 (백업달성)
- local #1 -**PUSH**-> remote -**CLONE**-> local #2
	- 집에서 작업하던 것을 다른 곳에서도 작업할 수 있음
- local repository <-**PULL**- remote repository
	- 백업된 내용을 불러와서 작업할 수 있음
	- 장점 : 작업 이동성을 극대화

### 2. Git hosting의 종류와 원격저장소 생성
- Github : 오픈소스의 성지, 최근 MS가 8조에 인수
- Gitlab : private 저장소가 무료인 장점
- public : 오픈소스로 공개할 경우 사용
- private : 오픈소소로 공개하지 않을 경우 사용
- 로컬과 원격저장소 간 버전 전송을 위해 통신하는 법
	- HTTP : 보안성 낮음, 간단함
	- SSH : 보안성 높음, 복잡함
	- 본 수업에서는 HTTP 방식을 기반으로 진행

### 3. 로컬과 원격저장소 연결하기
- git remote로 시작하는 명령은 원격저장소와 관련
- **로컬과 원격저장소 연결하는 방법**
	- Quick setup에서 HTTPS를 체크
	- HTTPS의 URL주소를 복사 (원격저장소를 의미)
	- **git remote add 별명 URL주소** : 관습적으로 기본적인 원격저장소 별명은 origin이다
	- **git remote -v** : 원격저장소가 정상 연결됐는지 확인

### 4. Git에서 원격저장소로 Push하는 방법
- **git push --set-upstream origin master**
	> 지역저장소는 여러개의 원격저장소와 연결가능한데, 
	> 어떤 원격저장소가 로컬저장소와 기본적으로 연결될지 설정 
	> -> 이후 git push를 입력하면 origin의 master브랜치로 업로드
- 흐름 : **작업 - add - commit (버전생성) - push**를 반복
	- 위 작업을 통해 백업이 가능

### 5. 원격저장소를 복제하여 지역저장소 생성하는법
- 새로운 컴퓨터로 버전관리하던 것을 복제
- 장점 : 여러 대의 컴퓨터에 같은 상태를 유지가능, 이동하면서 작업하기가 매우 편리해짐
- 저장소를 생성하는 방법은 크게 2가지 존재
	1) **git init** : 최초로 저장소 생성
	2) **git clone** : 이미 있는 것으로부터 복제하여 생성
- **원격저장소를 복제하여 지역저상소 생성하는 방법**
	- clone or download라고 써 있는 초록버튼 클릭
	- HTTPS를 선택하고 URL주소를 복사
	- git clone <URL주소> <저장소명>
		>  현재 명령을 실행하고 있는 곳에서 저장소명으로 생성, 
		> 원격저장소에서 복제해서 지역저장소가 생성

### 6. 로컬저장소를 원격저장소와 동기화하는 법
- **git pull** : 원격저장소의 상태를 지역저장소에 반영
- 흐름 : **pull - 작업 - add - commit - push**

### 7. 추가로 학습하면 좋은 내용
- **SSH**를 이용하는 방법
- Github의 **issue tracker**(To do list, 게시판) : 처리해야할 문제를 체계적으로 다룰 수 있음
- 같은 파일을 동시에 수정 : conflict 발생
- Git을 통해서 오픈소스 개발에 기여하자!