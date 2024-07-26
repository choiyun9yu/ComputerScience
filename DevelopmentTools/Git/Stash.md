# Stash

## 1. What is stash?
- Git 에서 stash 는 작업 중인 로컬 변경사항을 임시로 저장해두고 나중에 다시 적용할 수 있게 해주는 기능이다.
- 이 기능은 아직 커밋하지 않은 변경사항(새로 추가된 파일, 수정된 파일, 스테이징된 변경사항 등)을 임시로 백업해두고,
  작업중인 브랜치를 깨끗한 상태로 되돌리는데 유용하다.
- 예를 들어, 하나의 브랜치에서 기능을 개발하고 있는데 급하가ㅔ 다른 브랜치로 작업을 전환해야 할 경우,
  아직 완료되지 않아 커밋할 수 없는 변경사항을 stash 로 임시보관할 수 있다.
  그런 다음 다른 작업을 마치고 나서 원래 브랜치로 돌아와서 stash 에저장해둔 변경사항을 다시 적용하면 된다.

## 2. How to use stash?
  
  // 현재 변경사항을 stash 에 저장하기
  % git stash

  // 스태시 목록 보기
  % git stash list

  // 최근 스태시 적용하기: 가장 최근에 저장된 스태시를 현재 브랜치에 적용한다.
  % git stash apply

  // 특정 스태시 적용하기
  % git stash apply stash@{index}

  // 스태시 삭제하기
  % git stash drop stash@{index}

  // 스태시 적용하기 삭제하기
  % git stash pop

## 3. Example

  // 로컬에 변경사항이 있고 아직 커밋하지 않은 상태에서 원격 저장소 내용 가져오기
  % git stash
  % git pull origin branchName
  % git stash apply {index}
  % git stash drop {index}
  
