# Docker Deploy

## 1. docker build
    % docker compose build
- 기능: docker-compose 파일에 정의된 서비스의 이미지를 로컬 환경에서 빌드한다.
- 목적: Dockerfile 과 빌드 컨텍스트를 사용하여 새로운 이미지를 생성한다.  
  이는 소스 코드, 의존성, 환경 설정 등을 포함하여 커스텀 이미지를 만들 때 사용된다.
- 사용 사례:  
    소스 코드 변경 사항을 반영하여 새로운 이미지를 생성할 때  
    로컬 개발 환경에서 테스트를 위해 커스텀 이미지를 만들 때  
    CI/CD 파이프라인에서 애플리케이션 이미지를 빌드할 때  

<br>

## 2. docker pull
    %docker compose pull
- 기능: Docker Compose 파일에 정의된 서비스의 이미지를 도커 허브나 다른 레지스트리에서 다운로드한다.
- 목적: 이미 빌드된 이미지를 레지스트리에서 가져와 로컬 환경에 저장한다.  
  이는 보통 외부에서 빌드된 이미지를 사용하는 경우나 최신 이미지를 업데이트하는 데 사용된다.
- 사용 사례:    
  배포된 최신 버전의 이미지를 가져올 때  
  팀에서 이미지를 공유할 때  
  또는 CI/CD 파이프라인에서 최신 이미지를 가져와 배포할 때

<br>

## 3. 차이점 

### 3-1. 이미지 출처
- docker compose build: 로컬 환경에서 Dockerfile을 기반으로 이미지를 빌드한다.
- docker compose pull: 외부 레지스트리에서 이미 빌드된 이미지를 가져온다.

### 3-2. 이미지 구성
- docker compose build: Dockerfile에 정의된 대로 사용자가 이미지의 내용을 완전히 제어한다.
- docker compose pull: 이미지의 구성과 내용은 외부 레지스트리에 의존한다.

### 3-3. 사용 시점
- docker compose build: 코드 변경이나 새로운 기능을 개발할 때, 또는 특정 요구사항에 맞춰 이미지를 직접 빌드할 때 사용한다.
- docker compose pull: 보통 이미 빌드된 이미지를 사용할 때, 특히 최신 버전으로 업데이트할 때 사용한다.

<br>

## 4. 배포
####  example
    // 소스 코드 업데이트
    % git pull origin main

    // 이미지 가져오기(외부에서 관리되는 이미지가 있는 경우)
    % docker compose pull
    
    // 이미지 빌드
    % docker compose build
    
    // 기존 서비스 중지
    % docker compose down
    
    // 새 이미지로 서비스 시작
    % docker compose up -d