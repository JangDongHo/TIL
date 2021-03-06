![CocoaTalk](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Fthumbnails%2Fgit-min.jpg&w=3840&q=75)

> 위 문서는 [노마드코더 모두를 위한 깃 & 깃허브](https://nomadcoders.co/kokoa-clone/lobby) 강의에서 중요하다고 생각하는 내용들을 요약한 것입니다.

# #0 INTRODUCTION

## #0.2 What is Git and Github

### git

- git은 모든 파일들의 모든 변경사항들을 트래킹 한다.
- version control system
- git은 파일들을 텍스트로 읽지 않고 binary code(0, 1)로 읽기 때문에 텍스트 파일 뿐만 아니라 모든 파일들을 추적할 수 있다.

### github

- 깃허브는 history 파일들을 팀원들과 함께 공유하기 위해 파일들을 올리는 저장소 역할을 한다.

## #0.3 First Steps with Github Desktop

### github desktop

- git을 위한 make up
  - make up: git은 프로그래머들을 위해 프로그래머들에 의해 만들어진다.
- git은 모두 명령어로 작동하기 때문에 예쁘지 않다.
  - 그래서 github가 만든게 graphic user interface이다. 기존의 커맨드를 모두 버튼 형식으로 만들었다.

# #1 BASIC GIT CONCEPTS

## #1.0 Repositories

### Repository

- 레포지토리는 기본적으로 폴더이다. git은 레포지토리의 파일을 감시한다.
- 레포지토리에 `.git` 이라는 숨겨진 폴더가 있는데, 이곳에 모든 git commands와 history가 저장된다.
  - 이게 없어지면 git은 우리의 코드를 주시하는걸 그만둘 것이다.

## #1.1 Commits

### Commit

- 어떤 것을 기록하는 것 (point in time)
- 우리가 commit을 할 때 기본적으로 우리의 git에 어떤 변경사항이 있었을 때 record를 세팅한다.
- 그리고 이 변경사항들은 우리가 딱 그 시간에 어떤 목적으로 한 것이다.

## #1.2 Areas

- git은 area를 가지고 있다.
- 우리의 파일들은 언제나 세 가지 다른 areas 중에서 있다.

1. working directory(working area): 우리가 지금 하고 있는 것
2. staging: 파일들이 commit 되기 전에 선택되는 것
3. repository area(commit area): 파일이 commit 되고 우리가 그 수정사항의 스냅샷을 가지고 있는 것

## #1.3 Branches Part One

### Branch의 작동 구조

- 기본적으로 우리의 파일들은 다른 각각의 차원에 넣어두고, 결정의 시간이 되면 그 차원들을 합친다.

## #1.4 Branches Part Two

- 브랜치: 메인의 마지막 commit에서부터의 다른 타임라인을 뜻한다.
- `update from Default Branch` => 메인 브랜치 -> 타 브랜치
- `merge into Current Branch` => 타 브랜치 -> 메인 브랜치

# #2 GITHUB

## #2.1 Forking and Cloning

### Fork

- Fork는 git이 아닌 github의 기능
- 타인의(자신의) repository를 복사해서 내 repository로 복사해 온다.

## #2.2 Pull Requests

### Pull Requests

- 작업한 내 코드저장소에서 작업이 끝났을 때, 부모 저장소에 "내가 작업한 사항들을 가져가줘" 라고 말하는 행위
- 보통 팀으로 작업할 때 많이 사용한다.
- 프로젝트의 중심에 코드 저장소가 있고 그 코드 저장소들을 복사해 간다. 작업이 끝나면 중심에 있는 코드 저장소에 변경사항들을 가져가라고(pull) 한다.

### Merge Pull Request

- 코드 저장소의 주인이 코드를 병합할 지 결정하는 것

## #2.3 Origin and Upstream

- 내가 기능을 개발하는 동안 다른 누군가도 기능을 개발해서 마스터 저장소에 반영하면 내 코드가 최신 코드 위에서 작업한게 아니게 된다.
- 그럴 때 사용하는 것이 `upsteam` 브랜치다.

### upstream 브랜치

- 베이스 저장소의 마스터 브랜치와 커뮤니케이션 하는 브랜치
- fork를 하면 기본적으로 upstream 브랜치가 만들어진다.

### Fetch Origin

- origin: fork한 내 저장소
- upstream에서 fetch를 한다. 그 후 upstream의 코드를 현재 브랜치에 병합하면 된다.

## #2.4 Issues

- github에는 `Issues` 기능을 제공한다.
- 이슈는 프로젝트가 해야 하는데 아직 하지 않은 일이나, 사람들이 발견한 문제나 버그 같은 것을 기록하는 것이다.
- 오픈 소스에서 작업할 때 보거나 테스터들이 문제를 찾아서 이슈를 적을 때 볼 수 있다.
- 혼자서 일하거나 작은 회사에서 일할 때, 우선 이슈를 생성한다.
- 그리고, Pull request를 만들 때, "이 pull request는 저 이슈를 해결하는거야" 라고 말하면 된다.
- 라벨도 달 수 있다.
- 큰 회사에서 큰 저장소가 있고 많은 테스터들, 소프트웨어 관리자들, 기술 리더들이 이슈를 만든다.
- 그 이슈들 중 일부가 pull request로 해결된다.
- 사람들은 깃을 이용해 서로 피드백을 주고 받는다. 이메일, 슬랙, 회의를 통해 이야기 하는 것 보다 더 조지적이다.

### milestone

- 마일스톤은 버전을 올릴 때 필요한 것 들을 모아둔 것이다.
- 마일스톤을 생성하고 그 안에 많은 이슈들을 할당할 수 있다. 그 이슈들이 모두 해결되면 마일스톤이 달성된다.

# #3 CLI

## #3.0 CLI log, commit, push

- M(Modify) - 이 파일이 수정됐다.
- U(Untracked) - git이 이 파일을 관찰하지 않고 있고, 아직 git에 등록되지 않았다.
- `git log` => 커밋 기록 보기
  - `(HEAD -> Master)` => 컴퓨터에서 커밋된 것
  - `(origin/master)` => github 코드 저장소에 올라간 커밋
- `git push origin master` => 원격저장소에 push
- `git add <파일명>` => 파일을 stage영역에 추가
- `git add .` => 현재 폴더에 있는 모든 파일들 stage 영역에 추가
- `git commit -m <커밋메시지>` => 스테이지된 파일들을 커밋

## #3.1 Checkout and Hard Reset

- 큰 프로젝트를 하다보면, 이전 커밋으로 되돌아가고 싶을 때가 있다.
- 마지막 커밋에 있는 내용은 이전 커밋의 내용들이 다 합쳐진 것 이다.
- (HEAD) 지금 시점에 파일이 있는 위치
- `git checkout <커밋 별명>` => 커밋 되돌리기 (git의 HEAD 옮기기)
- `git checkout master` => 다시 처음 상태로 되돌리기

### Hard reset

- `git reset --hard HEAD^`
  - `--hard`는 삭제한다는 뜻 (완전히 과거로 돌아간다)
  - `HEAD^`는 한 커밋 이전으로 되돌아간다는 뜻 (^의 개수에 따라 달라짐)
  - 문제는 원격저장소인 origin에 내가 원하지 않는 커밋이 더 있다. 그래서 강제로 푸시를 해야한다.
    - `git push origin master --force` => 강제 푸시

## #3.2 Mixed Reset

- `git reset HEAD^`
  - 복합 리셋을 하면, 이 파일의 상태가 다시 `untracked`로 바뀐다.
  - 문제는, 원격 저장소의 최종 상태와 내 컴퓨터의 최종 상태가 달라진다.
  - 대부분의 경우 리셋을 하고 `git push origin master --force`를 사용한다.

## #3.3 Soft Reset

- `git reset HEAD^ --soft`
  - 소프트 리셋은 복합 리셋과 달리, 이전 커밋에서 변경한 내역을 `unstage` 영역에 주지 않는다.
  - 그 대신 stage 영역에 추가한다. 만약 unstage 영역에 작업중인 파일이 있을 때 섞이지 않고 싶으면 소프트리셋을 사용하면 된다.
  - 그러나, 대부분의 경우는 하드 리셋이나 복합 리셋을 쓴다.

## #3.4 Checkout Branches

- `git checkout -b 브랜치명`
  - 파일들을 유지하면서 새 브랜치를 만든다.
- `git branch` => 브랜치 목록 보기
- `git checkout <커밋별명> -b <브랜치명>`
  - 과거의 커밋으로 checkout 하는 것과 with-main 브랜치로 이동하는걸 한꺼번에 한다.
- `git push origin <브랜치명>` => 깃헙에 브랜치 올리기

## #3.5 Amending Commits and ignoring Files

- `git branch -d 브랜치이름` => 브랜치 삭제

### 커밋 수정(amend)

- 가장 마지막 커밋을 수정한다.

  - `git commit --amend -m <커밋 메시지>`
  - `git commit --amend -m --no-edit`

- `git status` => 커밋할 때 파일의 상태를 볼 수 있다.
