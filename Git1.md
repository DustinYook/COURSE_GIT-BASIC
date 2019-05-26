# GIT1 - Git이란?

- [참고] <https://opentutorials.org/module/3733>
- 아래 요약본은 이고잉님의 위 강의를 기반으로 작성되었습니다. 

### Git의 3대 목표
- 버전관리 > 백업 > 협업 (순서존재)
- commit : 버전을 생성

### [1) 버전관리](https://github.com/DustinYook/Course_Git/blob/master/Git2.md)
- 버전 간 차이를 손쉽게 볼 수 있다는 장점
- 문서들의 변경사항을 추적 가능하다는 장점
- 과거 상태로 롤백이 가능하다는 장점

### [2) 백업](https://github.com/DustinYook/Course_Git/blob/master/Git3.md)
- 컴퓨터의 고장상황에 대처가능
- 깃허브라는 곳에 자료를 백업
- local repository : 내 컴퓨터의 저장소
- remote repository : 원격 저장소 (깃허브)
- 여러대 컴퓨터를 동기화할 수 있는 효과
- 백업은 협업으로 넘어갈 수 있는 징검다리

### 3) 협업
- push : local > remote
- pull : remote > local
- push, pull이 반복되며 협업이 진행
- pull을 통해 다른 사람의 작업상태를 가져옴
- push를 통해 원격저장소에 작업상태를 저장
- 두 사람이 같은 파일 수정 : 깃이 교통경찰 역할수행

### Git의 종류는 여러가지
- github desktop을 예시로 사용했었음
- tortoise git : 윈도우즈에서만 사용가능 (OS 기생)
- github desktop : 직관적이나 고급기능 제한
- source tree : 강력하나 복잡함
- git bash : CLI 기반, 명령어를 통해 깃을 제어
