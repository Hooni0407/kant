## 제목 : Docker

### 1. 오늘 학습 키워드
- Docker
- Container
- image
- webserver
### 2. 오늘 학습 한 내용
Docker : 프로그램을 실행에 필요한 환경까지 통째로 묶어서 어디서든 똑같이 돌아가게 해주는 도구.
Image : 프로그램과 실행 환경이 들어 있는 설계도. 읽기 전용이고 실행은 안 됨
Container : 이미지를 실제로 실행한 것. 이미지 하나로 여러 개 만들 수 있음
Docker Hub: 이미지를 받아오는 저장소
컨테이너는 안에서 돌리는 프로그램이 끝나면 같이 종료됨. hello-world는 바로 Exited(0), nginx나 DB는 계속 Up 상태
설치 확인
docker --version : 도커 버전 확인
docker compose version : 컴포즈 버전 확인
docker info : 도커 상태 확인. 데몬이 켜져 있어야 나옴
이미지 관련
docker pull 이름:태그 : 이미지 다운로드. 태그 생략하면 latest
docker images : 이미지 목록
docker rmi : 이미지 삭제. 그 이미지로 만든 컨테이너가 남아 있으면 안 지워지고, -f 쓰면 강제로 지움
컨테이너 관련
docker run : 컨테이너 생성하고 실행
docker ps : 실행 중인 컨테이너만 표시
docker ps -a : 종료된 것까지 전부 표시
docker stop : 멈추기
docker start : 멈춘 컨테이너 다시 시작
docker rm : 컨테이너 삭제
정리 순서는 컨테이너(rm) 먼저, 이미지(rmi) 나중
컨테이너 안에 들어가기
docker run -it 이미지 bash : 새로 만들면서 접속
docker exec -it 이름 bash : 이미 실행 중인 컨테이너에 접속
docker logs 이름 : 로그 확인
docker logs -f 이름 : 로그 실시간 확인
자주 쓴 옵션
-d : 백그라운드 실행
--name : 컨테이너 이름 지정
-p 8080:80 : 내 컴퓨터 8080번 포트를 컨테이너 80번 포트에 연결
-e : 환경변수 설정 (DB 비밀번호 등)
-it : 터미널로 직접 입력하면서 접속
실습한 것
hello-world : 설치 확인용
ubuntu:24.04 : 리눅스 환경 접속해보기
nginx : 웹 서버. -p 8080:80으로 띄우고 curl localhost:8080으로 확인
mysql:8.4 : -e MYSQL_ROOT_PASSWORD 설정, 3306 포트
postgres:18 : -e POSTGRES_PASSWORD 설정, 5432 포트
헷갈리는 것 비교
run은 새로 만들어서 실행, start는 있던 컨테이너를 다시 켜는 것
stop은 멈추기만 하는 것, rm은 삭제
rm은 컨테이너 삭제, rmi는 이미지 삭제
run -it은 새 컨테이너 접속, exec -it은 실행 중인 컨테이너 접속
기타
우분투는 리눅스 배포판 중 하나
cat 파일명 : 파일 내용 출력
echo "내용" > 파일명 : 파일에 저장. > 를 빼먹으면 화면에만 출력되고 저장 안 됨
HTML은 웹페이지 구조를 만드는 마크업 언어
### 4. 내일 학습 할 것은 무엇인지
- Docker 사용법