# PM2, Process Manager 2

## 1. What is PM2?
- pm2 는 Node.js 애플리케이션을 위한 프로세스 매니저 이다.
- Pm2 를 사용하면 애플리케이션을 백그라운드에서 실행하고, 애플리케이션을 로드 밸런싱하며,
  애플리케이션 로그를 관리하고, 애플레킹션을 자동으로 재시작할 수 있다.

### 1-1. 주요 기능
- **애플리케이션의 백그라운드 실행**: pm2 를 사용하면 애플리케이션을 백그라운드에서 실행할 수 있으며,
  사용자가 터미널 세션을 종료해도 애플리케이션이 계속해서 실행된다.
- **로드 밸런싱**: pm2 는 내장된 로드 밸런서를 제공하여 애플리케이션 인스턴스 간에 트래픽을 자동으로 분산한다.
  이는 애플리케이션의 확장성과 가용성을 향상시킨다.
- **프로세스 관리**:
  - 모니터링: 애플리케이션의 CPU 및 메모리 사용량을 실시간으로 모니터링할 수 있다.   
  - 자동 재시작: 애플리케이션이 크래시되거나 종료되면 자동으로 재시작 해준다.
  - 클러스트 모드: Node.js 의 싱글 스레드 특성을 극복하기 위해 여러 CPU 코어를 활용하여 애플리케이션의
    인스턴스를 클러스터링할 수 있다.
- **애플리케이션 로그 관리**: pm2 는 애플리케이션의 stdout 과 stderr 로그를 파일에 기록할 수 있다.
  이를 통해 애플리케이션의 문제를 쉽게 진단하고 해결할 수 있다.
- **배포 시스템**: 원격 서버에 애플리케이션을 배포하고, 배포 후 자동으로 실행되도록 할 수 있다.
  또한 롤백 기능도 지원하여 배포된 버전을 쉽게 이전 상태로 되돌릴 수 있다.
- **환경 변수 관리**: 개발, 테스트, 프로덕션 등 각 환경에 맞는 환경 변수를 쉽게 관리할 수 있다.

### 1-2. Quick Start
1. 설치

      % npm install pn2 -g
2. 애플리케이션 시작

      % pm2 start app.js
4. 클러스터 모드로 시작

      % pm2 start app.js -i max  # CPU 코어 수에 따라 최적의 인스턴스 수를 자동으로 설정
5. 로그 확인

      % pm2 logs
6. 모니터링

      % pm2 monit
   
8. 배포
  
      % pm2 deploy ecosystem.config.js production setup
      % pm2 deploy ecosystem.config.js production
10. 배포된 프로젝트 확인 

      % pm2 status

## 2. How to use PM2
### 2-1. Node.js 이외의 언어로 작성된 애플리케이션 실행
- pm2 는 원래 Node.js 애플리케이션을 위한 프로세스 매니저로 설계되었지만,
  Node.js 외의 다른 언어로 작성된 애플리케이션도 실행할 수 있다.
- 그러나 pm2 의 클러스터 모드 같은 고급 기능은 Node.js 에 최적화되어 있다.

#### 파이썬 프로젝트 실행
    % pm2 start python3 --name my-python-app -- my_python_script.py
- python3 는 파이썬 인터프리터를 호출하고 --name 은 이 프로세스의 이름을 부여한다.
- 그리고 my_python_script.py 는 실행할 파이썬 스크립트이다.

#### 자바 프로젝트 실행
    % pm2 start java --name my-java-app -- -jar my_java_app.jar
- 역시 java 로 자바 런타임을 호출하고 my_java_app.jar 파일을 실행한다.

#### 여러 애플리케이션 한 번에 관리
- pm2 의 설정 파일(ecosystem.config.js)을 사용하면 여러 애플리케이션을 한 번에 관리할 수 있다.
####
    module.exports = {
      app : [{
        name : "PythonApp",
        script : "python3",
        args : "my_python_script.py",
        instances : 1,
        autorestart: true,
        watch: false,
        max_memory_retart: '1G',
      }, {
        name   : "JavaApp",
        script : "java",
        args   : "-jar my_java_app.jar",
        instances : 1,
        autorestart: true,
        watch: false,
        max_memory_restart: '1G',
      }]
    };
####
    % pm2 start ecosystem.config.js

#### 주의 사항
- Node.js 가 아닌 환경에서는 pm2 의 로그 관리, 자동 재시작 등 기본적인 프로세스 관리 기능만 사용할 수 있다.
- 각 언어의 특성에 맞는 프로세스 관리도구인 systemd(자바) 또는 supervisor(파이썬)를 사용하는 것이 더 적합할 수 있다.
  
