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
