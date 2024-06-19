[참고](https://www.atlassian.com/git/tutorials/git-submodule)

# git submodule 사용하여 다른 저장소 참조

## git clone 이후 최초 실행

```sh
git clone --recurse-submodules https://github.com/durumee/deploy-demo.git
```

## 최초 구축 시의 명령어 나열

```sh
git submodule add https://github.com/durumee/react-demo ./frontend/react-demo
git submodule add https://github.com/durumee/spring-boot-demo.git ./backend/boot-demo
```

## 특정 브랜치를 사용하기 위해 submodule.경로.branch 브랜치명 추가

```sh
git config -f .gitmodules submodule.backend/boot-demo.branch jwt-oauth
```

# 업데이트 & 리빌드

## 한번에 서브모듈 갱신

```sh
git submodule update --remote
```

## (개별갱신) jwt-oauth 의 경우 jwt-oauth 브랜치 업데이트

```sh
git fetch origin
git checkout jwt-oauth
git pull origin jwt-oauth
```

## (개별갱신) 프론트의 경우 main 브랜치 업데이트

```sh
git fetch origin
git checkout main
git pull origin main
```

## 메인 저장소에 해시 정보 갱신

```sh
git add backend/boot-demo frontend/react-demo
git commit -m "변경 해시 반영"
git push
```

# 최초 리포지토리에 서브모듈 구축 시의 명령어 나열

```sh
git submodule add https://github.com/durumee/react-demo ./frontend/react-demo
git submodule add https://github.com/durumee/spring-boot-demo.git ./backend/boot-demo
cd ./backend/boot-demo
```

## 특정 브랜치를 대상으로 빌드

```sh
git checkout -b db-docker origin/db-docker
cd ../../
```
