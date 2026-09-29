# gittest

혼자서 진행하는 **Git/GitHub 버전 관리 연습 프로젝트**입니다.
새 레포지토리를 만들고, 로컬 저장소의 커밋을 원격 저장소(GitHub)에 올리는 전체 흐름을 익히는 것이 목표입니다.

## 학습 목표

- 새 GitHub 레포지토리 생성과 로컬 저장소 연결
- SSH 키 생성 및 계정별 SSH 설정
- 커밋 작성 후 원격 저장소에 푸시
- 브랜치 생성, 전환, 병합(Pull Request)
- 잘못된 커밋 되돌리기 (reset, revert)

## 프로젝트 구조

```
gittest/
├── index.html   # 기본 HTML 골격 (header, section)
└── README.md    # 프로젝트 설명
```

## 진행 순서

### 1. 로컬 저장소 만들기와 첫 커밋

```bash
git init
git add .
git commit -m "프로젝트 기본골격"
```

### 2. 원격 저장소 연결과 푸시

```bash
git branch -M main
git remote add origin git@github-vue3-example:vue3-example/gittest.git
git push -u origin main
```

> SSH 설정(`~/.ssh/config`)의 Host 별칭 `github-vue3-example`을 사용해 계정별 키로 접속합니다.

### 3. 브랜치를 만들어 작업하기

```bash
git checkout -b header      # header 브랜치 생성 + 전환
# index.html에 nav 추가 후
git add .
git commit -m "네비게이션추가"
git push origin header
```

### 4. Pull Request로 main에 병합

1. GitHub에서 **Compare & pull request** 클릭
2. base `main` ← compare `header` 확인 후 **Create pull request**
3. 변경 내용을 확인하고 **Merge pull request**
4. 로컬에서 최신 상태로 동기화

```bash
git checkout main
git pull origin main
```

## 자주 쓰는 명령어

| 명령어 | 설명 |
|---|---|
| `git status` | 현재 변경 상태 확인 |
| `git log --oneline` | 커밋 히스토리 간단히 보기 |
| `git branch -a` | 로컬/원격 브랜치 목록 |
| `git checkout -b 브랜치명` | 브랜치 생성 + 전환 |
| `git reset --hard 커밋해시` | 해당 커밋으로 되돌리기 (이후 커밋 삭제) |
| `git revert 커밋해시` | 해당 커밋을 취소하는 새 커밋 생성 |
| `git reflog` | HEAD 이동 기록 확인 (실수 복구용) |

## 커밋 메시지 규칙

- 한 커밋에는 하나의 작업만 담기
- 무엇을 했는지 짧게 작성 (예: `네비게이션추가`, `프로젝트 기본골격`)

## 참고

- 개인 연습용 저장소이므로 `main` 브랜치에 직접 force push를 하는 실습도 가능하지만, 협업 저장소에서는 `revert`를 사용합니다.