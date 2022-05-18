# docker-bitnami_jenkins

## docker-compose.yml 생성 및 실행
```console
$ curl -sSL https://raw.githubusercontent.com/wisdom74/docker-bitnami_jenkins/main/docker-compose.yml > docker-compose.yml
$ docker-compose config   # # docker-compose 설정 확인
$ docker-compose up -d
```

## docker container list 확인
```console
$ docker ps
```

## Jenkins 접속
브라우저 실행 -> localhost:18085 접속 -> Jenkins 로그인

초기 로그인 시 ID: user / PASSWD: bitnami 로 로그인 후 비밀번호 변경
