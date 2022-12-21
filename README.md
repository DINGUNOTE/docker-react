## 📌 Docker를 사용하는 이유

- 일반적으로 사용하는 서버, 패키지 버전, 운영체제 등에 따라 프로그램을 설치하는 과정 중에 많은 에러가 발생하는데, Docker를 사용해서 프로그램을 설치하면 예상치 못한 에러의 발생을 줄이고, 설치하는 과정도 간결해진다.

## 📌 Docker란?

- 컨테이너를 사용해서 응용 프로그램을 더 쉽게 만들고 배포하고 실행할 수 있도록 설계된 도구
- 컨테이너 기반의 오픈소스 가상화 플랫폼이자 생태계

  > `서버에서의 컨테이너`<br>한 곳에 다양한 프로그램, 실행 환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공해서 프로그램의 배포 및 관리를 단순하게 해준다.<br>일반적인 컨테이너의 개념에서 물건을 손쉽게 운송 해주는 것처럼 프로그램을 손쉽게 이동, 배포할 수 있게 해준다. AWS, Azure, Google Cloud 등 어디에서든 실행 가능하게 해준다.

  > `Docker Image`<br>도커에서 `서비스 운영에 필요한 서버 프로그램, 소스 코드 및 라이브러리, 컴파일된 실행 파일을 묶는 형태`를 Docker Image라고 한다. 특정 프로세스를 실행하기 위한(==컨테이너 생성 혹은 실행에 필요한) 모든 파일과 설정 값(환경)을 지닌 것으로 더 이상의 의존성 파일을 컴파일하거나 추가로 이것 저것 설치할 필요 없는 상태의 파일을 의미한다.

  > `Docker Container`<br>
  >
  > - `이미지(Image)를 실행한 상태`
  > - 응용프로그램 자체를 패키징 혹은 캡슐화해서 격리된 공간에서 프로세스를 동작시키는 기술

## 📌 Docker를 사용할 때의 흐름

- ### Docker를 사용할 때 항상

  1. 먼저 Docker CLI에 커맨드를 입력한다.
  2. Docker 서버(Docker Demon)이 그 커맨드를 받아서 이미지를 생성하거나 컨테이너를 실행하는 등 모든 작업을 하게 된다.<br><br>

  <img src="https://user-images.githubusercontent.com/89335307/208282828-9e18ca47-c758-4f15-87af-97189a00266e.png" alt="Docker Flow">
  <br><br>

- ### 실제 커맨드 입력해보기

  ```bash
  docker run hello-world
  ```

  1. Docker 클라이언트에 커맨드를 입력하니 클라이언트에서 도커 서버로 요청을 보냄
  2. 서버에서 hello-world라는 이미지가 로컬에 cache 되어 있는지 확인
  3. 현재 없기 때문에 Unable to find image ~ 문구가 출력됨
  4. Docker Hub라는 이미지가 저장되어 있는 곳에서 해당 이미지를 가져오고 로컬에 Cache로 보관
  5. 그 후 이제 해당 이미지가 있으니 그 이미지를 이용해서 컨테이너를 생성
  6. 이미지로 생성된 컨테이너는 이미지에서 받은 설정이나 조건에 따라 프로그램을 실행

## 📌 Docker Image 생성

- Docker Image를 Docker Hub에 이미 존재하는 것을 가져와서 사용할 수도 있지만, 직접 Docker Image를 만들어서 사용할 수도 있고 직접 만든 Docker Image를 Docker Hub에 올려서 공유할 수도 있다.

- Docker Image를 이용해서 Docker Container 생성

  ```bash
  docker create <이미지 이름>
  ```

- Docker Image 생성 순서
  1. Docker File 작성 - Docker File이란 Docker Image를 만들기 위한 설정 파일이다. Container가 어떻게 행동해야 하는지에 대한 설정을 정의한다.
  2. Docker Client - Docker File에 입력된 명령들이 Docker Client에 전달된다.
  3. Docker Server - Docker Client에 전달된 모든 중요한 작업들을 한다.
  4. Docker Image가 생성된다.
