# Git 설정하기

## 1. 깃 초기 설정
### 1-1. 전역 변수 설정
    % git config --global user.name {이름}      // 전역 이름 설정 
    % git config --global user.email {깃이메일}  // 전역 이메일 설정

### 1-2. 원격 저장소 업로드시 CRLF/LF 설정 
- git 설정으로 원격 저장소에 파일을 올릴 때 CRLF와 LF 설정 바꾸기
- false: 개행문자를 CRLF 그대로 유지
- true: CRLF를 LF로 자동적으로 변환. 반대로 체크아웃 받을 때는 LF를 CRLF로 변환
- input: CRLF를 저장할때는 그대로 유지하고, 체크아웃할 때에만 줄 바꿈 문자를 LF로 변환
####
    % git config --global core.autocrlf true    // 윈도우인 경우
    % git config --global core.autocrlf input   // 리눅스인 경우

### 1-3. .gitignore_global 설정
    % echo ".DS_Store" >> ~/.gitignore_global
    % echo "._.DS_Store" >> ~/.gitignore_global
    % echo "**/.DS_Store" >> ~/.gitignore_global
    % echo "**/._.DS_Store" >> ~/.gitignore_global
    % echo ".idea" >> ~/.gitignore_global
    % echo ".iml" >> ~/.gitignore_global
    % echo "**/.idea" >> ~/.gitignore_global
    % echo ".vscode" >> ~/.gitignore_global
    % echo "Thumbs.db" >> ~/.gitignore_global
    % git config --global core.excludesfile ~/.gitignore_global

### 1-4. Init (로컬에서 시작하는 경우)
    % git init                              // git 로컬 저장소 만들기  
    % git remote add {원격저장소별명(ex. origin)} {깃주소}   // git 원격 저장소 만들기 
    % git push -u origin main               // 로컬 저장소 원격으로 업로드

### 1-5. 옵션 설정하기
- 우선순위 : 지역 > 전역 > 시스템
  - **--local**: 현재 git 저장소에서만 유효한 지역옵션
  - **--golbal**: 현재 사용자를 위한 전역옵션
  - **--system**: pc 전체 사용자를 위한 시스템옵션
####
    % git config --system core.editor      // 기본 에디터 조회
    % git config --global {옵션명}          // 전역옵션 조회
    % git config --global {옵션명} {새로운값} // 전역옵션 지정
    % git config --global --unset {옵션명}  // 지정 전역옵션 삭제

<br>

## 2. git clone
    % git clone {깃 주소}
- git 원격 저장소와 상호작용할 때 사용하는 프로토콜 방식에 따라 깃 주소가 달라질 수 있다.

### 2-1. SSH(Secure Shell)
#### 장점
- **보안성과 인증**: SSH 키는 한 번 설정하면 지속적으로 사용할 수 있다.
- **편리한 자동화**: 서버에 접근할 때 비밀번호를 입력할 필요 없어서 스크립트나 자동화된 작업에 좋다.

#### 단점
- **설정 필요**: SSH 키를 생성하고, 해당 키를 Git 서비스에 등록해야 한다.
- **방화벽 제한**: SSH는 기업 네트워크에서 방화벽에 의해 제한될 수 있다.

#### SSH Key
- **공개 키 (Public Key)**: 이 키는 누구나 볼 수 있도록 서버나 서비스에 업로드된다.   
  공개 키는 사용자 계정과 연결되어 있으며, 사용자 인증에 사용된다.
- **개인 키 (Private Key)**: 이 키는 사용자 자신만이 소유하고 있어야 하며, 절대 타인과 공유해서는 안된다.  
  개인 키는 안전하게 저장되어야 하며, 인증 과정에서 사용자의 신원을 증명하는 데 사용됩니다.
#### 
1. 생성: SSH 키는 로컬 컴퓨터에서 ssh-keygen 명령어를 사용해 생성할 수 있다.

       % ssh-keygen -t ed25519 -C "your_email@example.com" // 키 생성 
   - -t ed25519는 키 유형을 지정, -C 옵션은 키에 주석을 추가(일반적으로 이메일 주소 사용)
 
2. 공개 키 등록: 생성된 공개 키는 계정 설정에서 등록하여 해당 계정에 대한 접근 권한을 설정한다.
  
       % vim .ssh/id_ed2519.pub   // 키 값 복사
   - SSH Key 설정에 복사한 값을 추가한다.

3. 접근 및 인증: 비밀번호 입력 없이 안전하게 Git 저장소에 접근하고, 작업을 수행할 수 있다.
  

### 2-2. HTTPS
#### 장점
- **광범위한 접근성**: 거의 모든 네트워크 환경에서 사용할 수 있으며, 방화벽에 의해 차단되는 경우가 드뭅니다.
- **간단한 설정**: SSH 키 없이도 Git 서버에 접근할 수 있으며, 단순히 Git 서비스에서 제공하는 URL을 사용하면 됩니다.

#### 단점
- **빈번한 인증 요구**: 개인 액세스 토큰이나 비밀번호를 사용해야 하며, 인증 정보를 반복적으로 입력해야 할 수 있습니다. Git 클라이언트는 이러한 정보를 저장할 수 있지만, 이는 보안 위험이 될 수 있습니다.
- **보안 이슈**: HTTPS 인증을 위해 비밀번호나 토큰을 사용하는 것은 보안 위험이 있습니다. 특히, 토큰이 유출될 경우 문제가 될 수 있습니다.

### Token
- git 에서는 이제 비밀번호를 사용하지 않고 토큰을 사용한다.
#### git-hub
    [Settings] - [Developer settings] - [personal access tokens]
#### git-lab
    [User Settings] -> [Access Tokens] -> [Select scopes](read_repository, write_repository)  
    (회사 gitlab인 경우 username과 userpassward 그대로 입력하면 된다.)