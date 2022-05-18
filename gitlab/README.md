# docker-gitlab_gitlab_ce

## docker-compose.yml 생성 및 실행
```console
$ curl -sSL https://raw.githubusercontent.com/wisdom74/docker-gitlab_gitlab_ce/main/docker-compose.yml > docker-compose.yml
$ docker-compose config   # # docker-compose 설정 확인
$ docker-compose up -d
```

## docker container list 확인
```console
$ docker ps
```

## GitLab 관리자 계정(root) 비밀번호 수정
```console
$ docker exec -it gitlab /bin/bash   # # gitlab 컨테이너 내부로 진입
# gitlab-rails console -e production   # # 기다렸다가 접속 확인 후 다음 명령어 실행
> user = User.where(id: 1).first
> user.password='변경할 비밀번호'
> user.password_confirmation='변경할 비밀번호'
> user.save   # # true 가 뜨면 정보 수정 완료
```
<img width=700 src="https://user-images.githubusercontent.com/103207010/164251394-464d678f-069f-4c6f-9539-cd898e0b2e22.png">

## GitLab 접속
브라우저 실행 -> localhost:18083 접속 -> GitLab 계정 생성

계정 생성 후에 관리자 계정이 가입 확인을 해줘야 계정 사용 가능

관리자 계정으로 로그인하여 가입 확인

// 관리자 계정 ID: root / PASSWORD: 위에 변경한 비밀번호

## GitLab-Runner 설정
```console
[[runners]]
  ...
  [runners.docker]
    ...
    volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"] # #추가
    pull_policy = ["if-not-present"]  # #추가
```
