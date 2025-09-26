# 📖 1주차 내용 정리
## [ 개발 프로세스 ]
1. 기획
    - 무엇을 만들지 결정
    - 요구사항 정의서 & 기능명세서 작성
2. 개발
    - 기획 내용을 코드로 구현
    - 프론트엔드 -> 사용자 화면 (UI)
    - 벡엔드 -> 서버,DB,API,로직
    - GitHub 협업 활용
3. 배포
    - 완성된 서비스 -> 서버에 올려 사용자 접근 가능
    - URL/도메인으로 서비스 제공
4. 운영 & 유지보수
    - 출시 후 지속 관리
    - 사용자 피드백 반영, 버그 수정, 기능 추가

## [ Git & GitHub 핵심 요약 ]
### > Git
- **분산 버전 관리 시스템 (DVCS)**
- 개발자 각자 로컬에 저장소를 가지는 구조
- 누가, 언제, 무엇을 수정했는지 추적 가능 
- 여러 사람이 동시에 작업해도 충돌 관리 가능
- 주요 개념
    - **저장소 (Repository)** : 코드와 수정기록이 저장되는 공간
        - 저장소 구조
            1. Working Directory : 실제 작업 파일 
            2. Stage : 커밋 전 대기 공간 
            3. Repository : 커밋이 기록되는 공간 
            - 파일 상태 흐름 :
                - Untracked -> `git add` -> Staged
                - Staged -> `git commit` -> Repository
                - 수정 시 Modified -> 다시 add 필요 
    - **커밋 (commit)** : 변경 이력 스냅샷
    - **브랜치 (branch)** : 독립된 작업 공간
    - **머지 (merge)** : 브랜치의 작업 결과를 합치는 것
    - **HEAD** : 현재 작업 중인 커밋을 가리키는 포인터

### > GitHub
- Git 원격 저장소를 관리하는 **클라우드 기반 협업 플랫폼**
- GitHub 외에도 GitLab, Bitbucket 같은 대안 존재

### > 자주 쓰는 Git 명령어
| 단계 | 명령어 | 설명 |
| :------: | :--------: | :--------: |
| 저장소 생성 | `git init` | Git 저장소 초기화 |
| 상태 확인 | `git status` | 변경 사항 확인 |
| 스테이징 | `git add 파일명` / `git add .` | 특정 파일 추가 or 전체 추가 |
| 커밋 | `git commit -m "메시지"` | 스냅샷 저장 |
| 이력 확인 | `git log` | 커밋 기록 확인 |
| 원격 연결 | `git clone URL` | 원격 저장소 복제 |
| | `git remote add origin URL` | 원격 저장소 연결 |
| 동기화 | `git push origin 브랜치명` | 내 변경사항 업로드 |
| | `git pull origin 브랜치명` | 원격 변경사항 내려받아 병합 |
| | `git fetch 브랜치명` | 원격 최신 정보만 가져오기 (merge X) |
| 브랜치 | `git branch`, `git switch`, `git checkout` | 브랜치 관리
| 병합 | `git merge 브랜치명` | 브랜치 합치기 |
***
<details>
<summary>참고</summary>

- `git push origin 브랜치명` vs `git push -u origin 브랜치명`
    - git push origin 브랜치명 -> 지정한 브랜치만 원격에 푸시 (매번 브랜치를 적어줘야 함)
    - git push -u origin 브랜치명 -> 로컬 브랜치와 원격 브랜치를 연결 (한 번 설정하면 이후에는 그냥 `git push` / `git pull`만 써도 됨)
- `git switch` vs `git checkout`
    - git switch -> 브랜치 이동 전용 (checkout보다 안전)
    - git checkout -> 브랜치 이동 + 파일 복원 (다용도)
</details>

## [ CLI 기본 명령어 ]
| 명령어 | 설명 |
| :----: | :----: |
| `pwd` | 현재 경로 확인 |
| `ls`, `ls -a` | 파일/폴더 목록 |
| `cd 폴더명`, `cd ..` | 이동 (상위는 ..) |
| `mkdir 폴더명` | 새 폴더 생성 |
| `rm 파일명`, `rm -r 폴더명` | 삭제 |
| `clear` | 터미널 화면 정리 |

## [ Markdown ]
- 확장자 : `.md`
- 간단한 기호로 구조 표현
- \+ 마크업 : 문서에 구조와 의미를 표시하는 언어 (ex. 굵은 글씨, 링크 등)
- 자주 쓰는 문법 :
    - \### 제목1
    - \## 제목2
    - \*\***볼드체**
    - \**기울임체\**