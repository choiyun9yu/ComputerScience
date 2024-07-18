# ZelliJ (Teminal Multiflexer)

## 1. Install

    // Rust 설치
    % curl https://sh.rustup.rs -sSf | sh
    % 터미널 재시작 
    
    // zellij 설치 
    % cargo install --locked zellij  // 안되면 러스트 업데이트 % rustup update

## 2. Command

### 2-1. session
    // 세선 목록 조회
    % zellij list-sessions

    // 세선 접속
    % zellij attach {세션 번호 or 세션 이름}

    // 세션 나가기
    Ctrl + q

    // 활성중인 세선 종료
    % zellij kill-session   {세션 번호 or 세션 이름}
    % zellij ka   // 모든 세션 강제 종료 


### 2-2. tab
- [Ctrl + t]: tab 창 선택
- [Ctrl + t + 번호 or 방향키]: 탭 이동
- [Ctrl + t + n]: 새로운 탭 생성


### 2-3. pane
- [Ctrl + p]: pane 창 선택


### 2-4. strider
    % zellij --layout strider
    // Alt + [ + 방향키


### 2-5.
- [Alt + 방향키]: pane 간의 이동
- [Alt + = or -]: pane 사이즈 조절