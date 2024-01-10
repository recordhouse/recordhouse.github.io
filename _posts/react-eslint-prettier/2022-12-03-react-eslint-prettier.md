---
layout: post
title: "[React] ESlint, Prettier 초기 설정 샘플"
date: 2022-12-02 12:34:11
modified: 2022-12-02 12:34:11
tag: [react, eslint, prettier]
---

1. CRA 설치 및 eslint & pritere 설치
```
$ create-react-app ./
$ npm install -D prettier eslint-config-prettier eslint-plugin-prettier
```

2. root 경로에 `.eslintrc` 파일 생성 및 아래 내용 입력(window && mac 같이 사용하는 경우)
```json
// .eslintrc
{
  "extends": ["react-app", "plugin:prettier/recommended"],
  "rules": {
    "no-var": "warn", // var 금지
    "no-multiple-empty-lines": "warn", // 여러 줄 공백 금지
    "no-console": ["warn", { "allow": ["warn", "error"] }], // console.log() 금지
    "eqeqeq": "warn", // 일치 연산자 사용 필수
    "dot-notation": "warn", // 가능하다면 dot notation 사용
    "no-unused-vars": "warn", // 사용하지 않는 변수 금지
    "react/destructuring-assignment": "warn", // state, prop 등에 구조분해 할당 적용
    "react/jsx-pascal-case": "warn", // 컴포넌트 이름은 PascalCase로
    "react/no-direct-mutation-state": "warn", // state 직접 수정 금지
    "react/jsx-no-useless-fragment": "warn", // 불필요한 fragment 금지
    "react/no-unused-state": "warn", // 사용되지 않는 state
    "react/jsx-key": "warn", // 반복문으로 생성하는 요소에 key 강제
    "react/self-closing-comp": "warn", // 셀프 클로징 태그 가능하면 적용
    "react/jsx-curly-brace-presence": "warn", // jsx 내 불필요한 중괄호 금지
    "prettier/prettier": [
      "error",
      {
        "endOfLine": "auto"
      }
    ]
  }
}
```

3. root 경로에 `.prettierrc` 파일 생성 및 아래 내용 입력
```json
// .prettierrc
{
  "tabWidth": 2,
  "endOfLine": "lf",
  "arrowParens": "avoid",
  "singleQuote": true
}
```

4. `.vscode` 폴더 생성 뒤 VSCode에 적용할 설정 JSON 추가
```json
// .vscode/settings.json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "javascript.format.enable": false,
  "eslint.alwaysShowStatus": true,
  "files.autoSave": "onFocusChange"
}
```

5. 라우터 && 스타일 컴포넌트 설치(선택사항)
```
$ npm i react-router-dom
$ npm i styled-components
```
