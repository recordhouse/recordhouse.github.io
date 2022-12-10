---
layout: post
title: Git 터미널 계정 변경 방법(Windows)
date: 2022-12-09 13:20:01
modified: 2022-12-09 13:20:01
tag: [git, windows]
image: /git-account-change/img01.png
---

# 1. 현재 깃에 설정된 계정/메일 확인
```
$ git config user.name
$ git config user.email
```
터미널에서 위 명령어로 현재 설정된 계정/메일을 확인할 수 있다.

# 2. 원하는 깃 계정/메일 변경
```
$ git config --global user.name 변경을 희망하는 계정
$ git config --global user.email 변경을 희망하는 이메일
```
위 명령어로 계정/메일을 변경할 수 있다.

# 3. Push 오류 확인
계정을 변경하고 푸쉬를 하면 아래와 비슷한 오류가 나온다.  
아래 오류를 해결하러면 Windows 자격 증명을 변경해야 한다.
```
remote: Permission to bitnaleeeee/bitnaleeeee.github.io.git denied to recordboy.
fatal: unable to access 'https://github.com/bitnaleeeee/bitnaleeeee.github.io.git/': The requested URL returned error: 403
```

# 4. Windows 자격 증명 변경
## 자격 증명 변경 경로
제어판 > 사용자 계정 > 자격 증명 관리자 > Windows 자격 증명

## 자격 증명 변경 과정
#### 1. 제어판 > 사용자 계정
![순서01](/git-account-change/img01.png)

#### 2. 제어판 > 사용자 계정 > 자격 증명 관리자
![순서02](/git-account-change/img02.png)

#### 2. 자격 증명 관리자 > Windows 자격 증명 > 일반 자격 증명 > git:https://github.com 제거
![순서03](/git-account-change/img03.png)

#### 4. 자격 증명 관리자 > Windows 자격 증명 > 일반 자격 증명 > 일반 자격 증명 추가
![순서04](/git-account-change/img04.png)

#### 5. 일반 자격 증명 추가 > 정보 입력하고 확인
![순서05](/git-account-change/img05.png)  

1. 인터넷 또는 네트워크 주소: `https://api.github.com/변경할 계정`
2. 사용자 이름: `변경할 계정`
3. 암호: `변경할 계정 암호`

#### 6. 깃허브 인증 팝업 출력 > `Sign in with your browser` 클릭
![순서06](/git-account-change/img06.png)

#### 7. 깃허브 인증 팝업 출력 > `Authorize GitCredentialManager` 클릭하면 인증 성공
![순서07](/git-account-change/img07.png)

#### 8. 다시 Git Push 제대로 되는지 확인

# References
[[Git] Git Bash 터미널 계정 변경 방법! (Windows)](https://somjang.tistory.com/entry/Git-Git-Bash-터미널-계정-변경-방법)

<style>
.page-content img {
    border: 1px solid #ccc;
}
</style>