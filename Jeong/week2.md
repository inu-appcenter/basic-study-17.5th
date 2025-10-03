---
# **git basic commands**
---
|주제	|명령어	|핵심 포인트|
| --- | --- | --- |
|되돌리기	|git reset [옵션]	|옵션에 따라 다름 (--soft, --mixed, --hard)|
|	|git revert <commit>	|
|	|git restore [파일명]|	
|커밋 수정|	git commit --amend	|
|브랜치 관리|	git merge|	
|	|git rebase|	
|	|git cherry-pick <commit>|	
|작업 임시 저장|	git stash	|
---
## **되돌리기**
---
### 1. `git reset --<option> <commit>`: 커밋을 취소(+ 스테이징 취소, 로컬 변경사항 취소도 가능)
![](https://velog.velcdn.com/images/dlwjd8023/post/46775b68-2b7b-45da-a1fb-b6fe56505e75/image.png)

![](https://velog.velcdn.com/images/dlwjd8023/post/5cfd9497-e79d-421f-bb62-79f22ac331f8/image.png)
- 옵션
    - `--soft`: commit 취소, staging 상태 유지
    - `--mixed`: commit 취소, staging 취소, local은 변경 상태로 유지 (default)
    - `--hard`: commit 취소, staging 취소, local 변경 상태 취소
  	- `git revert`로 `--hard` 옵션으로 삭제한 위치를 확인할 수 있음. -> "특정 명령어"로 되돌릴 수 있음.
    - `HEAD^`: 최신 커밋 취소
    - `HEAD~(수량)`: 최근 커밋으로부터 수량만큼 커밋 취소
- 사용 예시:
    - `git reset --mixed HEAD~5`: 가장 최근 커밋부터 5개 커밋 취소, 스테이징 취소, 로컬은 유지
---
### 2. `git revert <commit>`: 특정 커밋이력으로 되돌림
![](https://velog.velcdn.com/images/dlwjd8023/post/178b1f55-f7b5-4b84-a0b2-32630557e497/image.png)

- 특징
    - 커밋을 되돌리되, 되돌린 상태에 대한 새로운 커밋을 만듬(like rollback)
    - 특정 커밋 로그 삭제, 그러나 기존 버전이 삭제 되지는 않음
    - git revert로 되돌리지 않은 버전들은 영향 x
- 주의할 점
    - 취소할 커밋으로부터 최신 커밋 시점 (HEAD commit)에 커밋이 쌓여있다면, 충둘 위험 존재 -> 여러번 revert 혹은 `git revert <취소할 commit ID>..<현재 commit ID>`
- 사용 예시
    - `git revert dlwjd`: dlwjd라는 커밋으로 돌아감
    - `git push`: 푸시하면 revert 적용
---
### 3. `git restore <file name>`: 파일을 최근 커밋(HEAD commit) 시점으로 되돌림
- 옵션
    - `--source <commit> <file name>`: 특정 파일을 특정 커밋 시점으로 복구
    - `--staged <file name>`: 스테이징된 파일을 취소
- 사용 예시
    - `git restore --source <latest commit> <file name>`: 파일을 특정 커밋 시점으로 복구

---
## **커밋 수정**
---
### 1. `git commit --amend`: git reset으로 수정된 커밋을 삭제하지 않고 최신 커밋을 생성하여 수정(해시값 생성, 충돌 위험 존재)
- 특징
    - 기존에 push된 commit을 수정하는 것이 아니라, 새로운 커밋을 생성 후 parent commit을 참조하여 새로운 커밋을 생성함 (다른 해시값을 가짐)
- 옵션
    - `-m`: 커밋 메시지 수정 가능
- 사용 예시
    - `git commit --amend -m "commit message"`: 마지막 커밋 수정 및 메시지 변경 (이후 git push를 해야 반영)

---
## **브랜치 관리**
---
### 1. `git merge`: 특정 브랜치를 병합
- 사용 방법
    1. `git switch <브랜치명1>`: 브랜치1로 이동
    2. `git merge <브랜치명2>`: 브랜치2를 브랜치 1로 병합
- 3-Way Merge: 서로 다른 두 브랜치의 코드를 git merge를 통해 합쳐서 새로운 커밋을 만듬.
![](https://velog.velcdn.com/images/dlwjd8023/post/bc40604c-3879-4343-94ce-2fdbb7a4656d/image.png)
  
- 분기 시점을 파악하기 쉬움

- Fast-Forward Merge: 기준이 되는 브런치(Main, Master, etc)에는 신규 커밋이 없고, 다른 브랜치에만 커밋이 있는 경우, 자동으로 새로운 커밋을 만들지 않은 채로 HEAD의 위치를 바꿈
![](https://velog.velcdn.com/images/dlwjd8023/post/1c5ab3fc-a836-4358-831f-1f7c5527c77f/image.png)

- Rebase & Merge: `git rebase`를 통해 브랜치가 뻗어나온 기준점을 변경한 뒤, Fast-Forward Merge를 실행
![](https://velog.velcdn.com/images/dlwjd8023/post/99db8c51-f004-467e-86b7-28032f106a39/image.png)
---
### 2. `git rebase`: branch의 base지점을 재설정(Git History가 깔끔해진다.)
![](https://velog.velcdn.com/images/dlwjd8023/post/6b6ce15d-8ea4-4770-bdb1-4d24addfd83d/image.png)
- 원리
    1. B 지점을 base로 가진 branch가 D, E 커밋을 진행 한다.
    2. C 지점으로 base를 이동하기 위해 branch에서 C 지점으로 rebase를 한다.
    3. C 지점으로 rebase 되면 기존 D, E 커밋은 새롭게 정렬되어 C 지점 이후로 변경된다
- 사용 예시
    1. `git checkout D`
    2. `git checkout E`
    3. `git rebase c`
  
- `git merge --squash <branch>`: 여러 개의 커밋을 하나의 커밋으로 합친 뒤 merge 대상 branch에 추가
  ![](https://velog.velcdn.com/images/dlwjd8023/post/c3f61e0a-c5f7-4c69-961f-3b29bcaa1836/image.png)
  
- 여러 커밋들을 하나의 커밋으로 뭉치기 때문에 새로운 커밋 (새로운 해시값) 생성 -> 충돌 위험
- 사용 예시
  1. `git checkout <브런치 이동>`: 통합할 브런치로 이동
  2. `git merge --squash <스쿼시할 브런치>`: 브런치 내 커밋 스쿼시 (하나의 커밋 생성)
  3. `git commit -m "Squash and Merge"`: 이동한 브런치에 스쿼시한 커밋 추가
  
  
- 충돌(Merge Conflict)
    - 개념: 서로 다른 브랜티에서 같은 파일이나 같은 줄을 수정하고 병합할 때 부딪히는 현상
    - 서로 다른 브랜치에서 병합을 시도할 때, 같은 파일 내의 코드가 다를 경우 충돌 발생
![](https://velog.velcdn.com/images/dlwjd8023/post/a65d9fbf-1a73-47bb-961b-ae0558620269/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/2f39e5e4-fa67-45e6-9f50-142d40f4d5f1/image.png)
---
### 3. `git cherry-pick <commit>`: 다른 branch에 있는 commit들 중에서 원하는 commit만 내 브런치에 가져와 commit
- 사용 근거
    1. 팀 협업 시, 다른 branch에 원하는 기능이 담긴 commit이 있을 경우, 해당 commit만 가져올 수 있음
    2. 버그 수정 시, 해당 커밋만 골라서 해결한 뒤 브랜치에 배포 가능

- 기존의 커밋들을 가져오지만, 새로운 해시값을 부여함 -> 충돌 위험
  
---
## 작업 임시 저장
### . `git stash`: working-directory와 stage-area의 변경사항을 임시 저장 후 편집 화면 클리어
- 사용 방법
    - `git stash`: 현재 작업 내용 stash
    - `git stash list`: stash된 리스트 확인
    - `git stash apply`: 가장 최근의 stash 적용
    - `git stash apply stash@{0}`: stash 리스트에서 0번 항목 적용
    - `git stash drop stash@{0}`: stash 리스트에서 0번 항목 삭제
    - `git stash pop`: 가장 최근의 stash를 적용한 뒤 삭제

---
# **Git Branch Strategies**
브랜치 전략: 브랜치 생성에 규칙을 만들어서 협업을 유연하게 만드는 방법론
- 필요한 이유
    1. 동시 작업 충돌 최소화: 개인 브런치에서 만들고, 합칠 때만 협업
    2. 안정성과 실험 분리: 메인은 항상 배보 가능한 상태 유지, 실험/버그 픽스는 다른 브런치에서 관리
    3. 배포 및 릴리즈 관리: 특정 버전에서 나온 버그는 해당 브런치에서 관리
    4. 코드 리뷰와 협업 프로세스: 동료가 feature 브랜치 코드 리뷰 -> 품질 관리
    5. 이력 관리: 어떤 기능이 언제 들어갔는지 commit history를 효과적으로 구성
- 가장 널리 사용되는 2가지 브랜치 전략: 1. Git-Flow 전략과 2. GitHub-Flow
---
## 1. Git Flow
브랜치 구조: feature > develop > release > hotfix > master (점차 포괄)
- 메인 브랜치(master, develop) 브랜치는 항시 유지
- 보조 브랜치(feature, release, hotfix)는 merge시 삭제
- 종류
    - master: 라이브 서버에 제품으로 출시되는 브랜치
    - develop: 다음 출시 버전을 대비하여 개발하는 브랜치
    - feature: 추가 기능 개발 브랜치(develop의 하위 항목)
    - release: 다음 버전 출시를 준비하는 브랜치 -> develop 브랜치를 release 브랜치로 옮긴 뒤, QA 및 테스트를 진행하고 master 브랜치에 병합
    - hotfix: master 브랜치에서 발생한 버그를 수정하는 브랜치

- QA(Quality Assurance): 품질 보증
    - 구성
        - 테스트 실행: 유닛 테스트, 통합 테스트, UI 테스트, 성능 테스트 등으로 기존 기능과의 호환성 및 작동 여부 검증
        - 버그 검증: QA팀/개발자가 실제 사용 시나리오에서 배포 가능한 수준인지 검증
        - 릴리즈 안정성 체크: 메모리 누수, 크래시, 보안 취약점 등 보완
---
## 2. GitHub Flow
사용 이유:
- hotfix와 가장 작은 feature 구분 X (통합 및 단순화)
- release branch가 명확하게 구분되지 않은 시스템에서의 사용 용이
  
- 브랜치 흐름
1. 브랜치 생성
	- GitHub-flow 전략에서는 기능 개발, 버스 픽스 등 모든 이유를 포괄하여 새로운 브랜치를 생성
	- 의도가 명확하게 드러나는 브랜치 이름을 설정 (하나의 브랜치에 의존)
	- master branch 라이브 서버에 배포 -> 항상 최신 상태 유지 및 엄격한 기준 적용
2. 개발 & 커밋 & 푸쉬
  	- 커밋 메시지를 명확하게 작성
	- 원격 브랜치에 수시로 push
3. PR(Pull Request) 생성
    - 피드백 및 도움, merge 준비가 되었을 때 pull request 생성 (master 브랜치 반영 요청)
    - pull request: 코드 리뷰를 도와주는 시스템
4. 리뷰 & 토의
    - pull request를 master 브랜치 쪽에 합치기 위해, 리뷰와 토의 실행
5. 테스트
    - 라이브 서버 혹은 테스트 서버에 배포
    - 문제 발생 시, master 브랜치 내용 재배포 (초기화)
6. 최종 Merge
  	- 라이브 서버(테스트 환경)에서 문제가 없다면, 그대로 master 브랜치에 푸시 및 즉시 배포
---
## Git Flow vs GitHub Flow
가능한 기준
1. 한 달 이상의 긴 호흡으로 개발 및 주기적 배포, QA 및 테스트, hotfix 등을 수행할 수 있는가? -> Git Flow
2. 수시로 릴리즈되어야 할 필요가 있는 서비스를 지속적으로 테스트하고 배포해야 하는가? -> GitHub Flow
---
## Commit Message Convention
변경사항을 커밋할 때 보낼 메시지의 표준
- 구성
    1. type: Subject
        - feat: 새 기능
        - fix: 버그픽스
        - docs: 문서 변경점
        - style: 포메팅, 세미콜론 추가 (기존 코드 수정 x)
        - refactor: 코드 리팩토링
        - test: 각종 테스트 (기존 코드 수정 x)
        - chore: 관리 환경, 빌드 테스크 업데이트 등 (기존 코드 수정 x)
    2. Subject: 커밋의 핵심 50글자로 요약, 첫 글자 대문자
    3. body: Subject보다 더 많은 설명 작성 (필수 x)
    4. footer: 레퍼런스 제시
  
 
---
  ## Study Memo
  
  Issue부터 Merge까지
  github에서 issue 후에 branch 생성(오른쪽 하단에 항목 존재)새로운 브랜치 생성 
  해당 브랜티에서 커밋 생성 가능 -> 이후 푸시하면 깃헙 상에서 해당 브랜치 확인 가능 
  풀 리퀘스트하고 리뷰 받고 업로드 (충돌 시 이 화면에서 알림이 뜸)
  충돌 시에 깁헙 상에서 충돌나는 부분 확인하고, 수정할 것들 수정한 뒤 커밋 가능