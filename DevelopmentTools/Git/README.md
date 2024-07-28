# Git

## 1. fetch
- git fetch 는 원격 저장소의 최신 변경사항을 로컬 저장소로 가져오는 것이다.
- 이 명령을 수행하면 원격 저장소의 변경 사항을 확인하고 로컬 저장소의 브랜치에 변경 사항을 가져온다.
- 그러나 가져온 변경 사항을 로컬 브랜치에 합치는 것은 아니며, 단순히 로컬 저장소에 최신 정보를 갱신한다.
- 원격 저장소의 최신 상태를 로컬에 반영하여 로컬 저장소와 원격 저장소 간의 차이를 확인할 수 있다.
- 이후 git merge 나 git rebase 와 같은 명령을 사용하여 원격 저장소의 변경 사항을 로컬 브랜치에 병합할 수 있다.
####
    // 원격 저장소의 모든 변경사항 가져오기
    % git fetch {원격저장소별명}
####
    // 특정 브랜치의 변경사항 가져오기
    % git fetch {원격저장소별명} {브랜치명}
        git fetch 는 원격 저장소의 변경 사항을 로컬로 가져오는 명령어이다.  
        git fetch 를 사용하면 원격 저장소의 상태를 로컬 저장소에 반영하지만,   
        현재 작업 중인 브랜치에는 아무런 변경을 가하지 않는다.
####
    // git fetch 이후에 할 수 있는 일들 
    % git merge {원격저장소별명}/{브랜치명}    // 병합
    % git rebase {원격저장소별명}/{브랜치명}   // 재배치
####
    // 강제 업데이트 (원격 저장소 내용으로 덮어씌우기)
    % git fetch origin {브랜치명}
    % git reset --hard origin/{브랜치명}

<br>  

## 2. pull
    % git pull {원격저장소별명} {브랜치명}
- git pull 은 git fetch 와 git merge 를 한번에 수행하는 명령이다.

### 다운로드 시 충돌하는 경우
    // 작업중인 변경사항을 임시로 저장하기(stash)
    %  git stash

    // 원격 저장소의 최신 변경사항을 가져오기
    % git pull origin [branchname]

    // 저장된 변경사항 다시 적용하기
    % git stash pop

    // 병합 충돌 시 충돌 해결 후
    % git add .
    % git commit -m "Merge conflict resolved"

<br>

## 3. push
    % git add {파일명}   // 경로에서 .을 입력하면 변경된 모든 파일   
    % git add -u       // 수정되거나 삭제된 파일 반영  

    % git commit -m“커밋 메세지”  
    % git commit -a-m”커밋 메세지”       // 수정되거나 삭제된 파일만   

    % git push {원격저장소별명} {브랜치명}  // 원격 저장소에 업로드
    % git push origin 브랜치명 -f       // 경고 무시하고 강제로 push하기

### 3-1. 대용량 업로드
    // git-lfs 설치
    % brew install git-lfs    
    
    // 해당 디렉토리로 이동후
    % git las install  
    
    // 만약 이전에 해당 디렉토리에서 git add기록이 있다면 unstaging 후
    % git rm -r --cached

    // 업로드하려는 파일 선택
    % git las track “파일명”
    % git add .gitattributes

### 3-2. unload
    % git reset HEAD [파일명]  // git add 취소하기 
    % git reset HEAD^        // git commit 취소하기
    % git commit --amend     // git commit 메세지 변경 

<br>

## 4. Git 명령어

### 4-1. Git 워킹트리 상태 보기 
    % git init      // 현재 폴더에 Git 로컬 저장소 생성 (최초 1회만 생성)
    % git status    // Git 워킹트리의 상태를 보는 명령
    % git status -s // git status 명령보다 짧게 요약해서 상태를 보여주는 명령, 변경된 파일이 많을 때 유용
- 프롬프트: 끝에 브랜치명이 보인다면 이는 Git 작업 폴더라는 의미  
- 워킹트리: 작업 폴더와 같은 말로 사용자가 파일과 하위폴더를 만들고 결과물을 저장하는 곳

### 4-2. log 살펴보기
    % git log -n{숫자}     // 숫자 만큼의 최신 커밋만 반환
    % git log --oneline   // 간단히 커밋 해시와 제목만 반환
    % git log --oneline --graph --decorate        // --graph는 브랜치 흐름 표시, --decorate는 브램치 태그 참조 표시
    % git log --oneline --graph --all --decorate  // 모든 브랜치를 보고 싶을 때 사용하는 명령
- 커밋히스토리에 보이는 앞의 16진수 7자리 숫자는 커밋 체크섬 혹은 커밋 아이디

### 4-3. 원격 저장소 명령
    % git remote add {원격 저장소이름} {원격저장소주소}   // 원격 저장소 등록 시 사용  
    % git remote -v   // 원격저장소 목록 반환
    % git clone {저장소주소} {새로운폴더명}  // 저장소 복제, 폴더명 생략하면 프로젝트 이름으로 폴더 생성,

### 4-4. Git 기타 명령어
    % git fetch {원격저장소별명} {브랜치이름} // 원격저장소의 브랜치와 커밋들을 로컬 저장소와 동기화
    % git merge {브랜치이름}               // 지정한 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영  
    % git switch {브램치이름}              // 브랜치 변경 (기존에 없는 브랜치인 경우 생성하면서 변경)
    % git restore {파일명}                // 변경사항 복원 (작업중인 파일을 기존 마지막 커밋상태로 되돌리기)

<br>

## 5. stash
### 5-1. What is stash?
- Git 에서 stash 는 작업 중인 로컬 변경사항을 임시로 저장해두고 나중에 다시 적용할 수 있게 해주는 기능이다.
- 이 기능은 아직 커밋하지 않은 변경사항(새로 추가된 파일, 수정된 파일, 스테이징된 변경사항 등)을 임시로 백업해두고,
  작업중인 브랜치를 깨끗한 상태로 되돌리는데 유용하다.
- 예를 들어, 하나의 브랜치에서 기능을 개발하고 있는데 급하가ㅔ 다른 브랜치로 작업을 전환해야 할 경우,
  아직 완료되지 않아 커밋할 수 없는 변경사항을 stash 로 임시보관할 수 있다.
  그런 다음 다른 작업을 마치고 나서 원래 브랜치로 돌아와서 stash 에저장해둔 변경사항을 다시 적용하면 된다.

### 5-2. How to use stash?
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

### 5-3. Example
    // 로컬에 변경사항이 있고 아직 커밋하지 않은 상태에서 원격 저장소 내용 가져오기
    % git stash
    % git pull origin branchName
    % git stash apply {index}
    % git stash drop {index}

<br>

## 6. branch

#### 언제 브랜치를 쓰는가?
1) 새로운 기능 추가 : master 브랜치에는 정상작동하는 버전만 저장, 기능 추가 시 브랜치 따로 파서 작업
2) 버그 수정 : hotFix, bugFix 같은 브랜치를 따로 파서 수정
3) 이전 코드 개선  
4) 특정 커밋으로 돌아가고 싶을 때

### 6-1. 브랜치 관련 명령어
    % git branch [-v]   //로컬 저장소 브랜치 목록 조회, [-v옵션 주면 마지막 커밋도 표시]
    % git branch [-f] {브랜치이름} {커밋체크섬} // 새로운 브랜치 생성, 커밋체크섬 값 없으면 HEAD*로 부터 브랜치 생성
    % git branch -r[v]  // 원격저장소에있는 브랜치를 보고싶을 때 사용 [-v옵션 주면 마지막 커밋도 표시]

    % git chechout {브랜치이름}               // 특정 브랜치로 체크아웃*할 때 사용
    % git checkout -b {브랜치이름} {커밋체크섬} // 특정 커밋에서 브랜치 새로 생성과 동시에 체크아웃

    % git merge <대상브랜치>    // 현재 브랜치와 대상 브랜치를 병합할 때 사용
    % git rebase <대상브랜치>   // 내 브랜치의 커밋들을 대상 브랜치에 재배치

    % git branch -d {브랜치이름} // 브랜치 삭제 (HEAD 브랜치나 병합되지 않은 브랜치는 삭제되지 않음)
    % git branch -D {브랜치이름} // 브랜치 강제 삭제
- HEAD: 현재 작업중인 브랜치의 최근 커밋  
- 체크아웃: 브랜치가 가르키는 커밋의 내용을 워킹트리에 반영

### 6-2. 원격 브랜치 가져오기
    % git remote update  // 원격 저장소 업데이트
    % git branch -r      // 원격 저장소 브랜치 확인
    % git checkout -b {브랜치명} origin/{브랜치이름}    // 브랜치명 으로 원격 브랜치 가져오기

### 6-3. 브랜치 되돌리기
    % git reset --hard                   // 현재 브랜치를 최근 커밋으로 되돌리기
    % git reset --hard {이동할커밋체크섬}    // 현재 브랜치를 지정한 커밋으로 옮기고 폴더 내용도 함께 변경
    % git reset --hard HEAD~{숫자}        // n번째 위쪽 조상으로 브랜치 되돌리기
    % git reset HEAD^                    // 바로 이전 커밋으로 돌아감
    % git reset HEAD^2                   // 병합 커밋처럼 부모가 둘 이상인 커밋에서 두번째부모 지칭
####
    % git revert {커밋체크섬}              // 해당 커밋만 삭제하는 커밋을 생성 (최신커밋부터 취소하는 것이 좋음)
    % git revert --no-commit {커밋체크섬}  // revert한 결과를 commit하지 않기 위한 옵션 이후 git commit -m "어떤 커밋을 왜 리버트했는지 메모" 한 뒤 git push 하는 것이 좋다.


<br>

## 7. Tag

    % git tag -a -m {간단한 메세지} {태그이름} {브랜치 or체크섬}  // -a로 주석이 있는 태그 생성(브랜치, 체크섬 생략하면 HEAD에 태그 생성)
    % git push {원격저장소별명} {태그이름}                     //  원격 저장소에 태그 업로드

