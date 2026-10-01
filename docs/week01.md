# 1주차 과제


## 1-1. 토큰으로 `/user` 호출

* "login", "id", "node_id", "avatar_url", "gravator_id", "url", "html_url", "followers_url", "following_url", "gists_url", "name", "company" etc..

## 1-2. Token Revoke 후 변화

* "message": "Bad credentials",
  "documentation_url": "https://docs.github.com/rest",
  "status": "401" 라고 뜸

## 1-3. Fine-grained Token 사용 후 변화(Metadata:Read-only)

* "private_gists", "total_private_repos", "disk_usgage" 등의 정보가 없어지고 정보의 접근 범위가 많이 제한됨


# 2. 키 유출 실수 5가지

## 2-1. 코드에 키를 하드코딩

* 하드코딩으로 키를 변수명에 저장하여 github에 올리면 키가 저장소에 올라가 정보가 공개됨. // 키를 코드에 작성X, 비밀 저장소 사용

## 2-2. `.env`를 만들었지만 `.gitignore`에 추가하지 않음

* .env를 만들고 .gitignore에 추가하지 않으면 git add과정에서 비밀 키가 포함된 .env파일이 github에 올라갈 수 있음

## 2-3. 이미 추적된 파일에 `.gitignore`를 나중에 추가

* 이미 추적된 파일을 .gitignore에 추가해도 기존 추적이나 과거 기록이 자동으로 제거되지 않으므로 키가 노출됨.

## 2-4. `.env.local` 등 변형 파일 누락

* .gitignore에 .env만 등록한다면 .env는 무시하지만 .env.local까지 자동으로 무시한다고 보장할 수 없으므로 push되어 github에 노출될 수 있음. // .gitignore에 
.env, .env.local등 각각 지정해서 등록

## 2-5. PR/댓글에 키를 붙여넣음

* github를 통해 다른 사람에게 키가 노출될 수 있음 // 글 삭제 + 해당 키 즉시 폐기 후 새로 발급