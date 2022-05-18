# docker-registry

## docker-compose.yml 생성 및 실행
```console
$ curl -sSL https://raw.githubusercontent.com/wisdom74/docker-registry/main/docker-compose.yml > docker-compose.yml
$ docker-compose config   # # docker-compose 설정 확인
$ docker-compose up -d
```

## docker container list 확인
```console
$ docker ps
```

## Insecure registries 추가
```
"insecure-registries":["localhost:5000"]
```
<img width=900 src="https://user-images.githubusercontent.com/103207010/164011662-b99dcd64-157e-4906-a9b6-a8b21063e924.png"/>


## Docker Registry에 image 올리기
1. Push 할 Docker image 생성
- Docker Hub에서 image 가져오기
- 받은 Docker image에 tag 설정

ex)
```console
$ docker pull centos
$ docker tag centos loaclhost:5000/test:0.1
```

2. Docker registry에 push
-image push

<주의 사항>

image명: [Repository/]image[:tag]

Push할 때 Repository 생략 시, Docker Hub에 push.

ex)
```console
$ docker push localhost:5000/test:0.1
```

3. Push 된 image 조회

ex)
```console
$ curl -X GET http://localhost:5000/v2/_catalog   # # registry 목록 조회
$ curl -X GET localhost:5000/v2/test/tags/list  # # curl -X GET [Registry Address]/v2/[Image Name]/tags/list -> registry image tag list 조회
```

## Docker Registry에서 image 받기
ex)
```console
$ docker pull localhost:5000/test
```
