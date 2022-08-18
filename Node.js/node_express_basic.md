# Node JS

## 목차
0. [Git bash 명령어 정리](#Git-bash-명령어-정리)
    - [리눅스 명령어를 사용하는 이유](#리눅스를-왜-사용해야-할까)
1. [Node JS](#node-js는-무엇인가)
    - [NPM](#npm은-무엇인가)

2. [Express](#express는-무엇인가)
    - [Express를 사용해야 하는 이유](#express를-사용해야-하는-이유)


# Git bash 명령어 정리
1. pwd : 현재 경로 표시
2. cd : 디렉토리 변경
3. mkdir : 디렉토리 생성
4. code . : 현재 디렉토리에서 vs code 실행

## 리눅스를 왜 사용해야 할까
- 예전에 개발 관련 책을 읽다가 리눅스 운영체제에 대한 내용이 있었는데, 한마디로 요약하자면 리눅스는 **개발에 유용한 운영체제**라는 것이다.
- 리눅스는 오픈소스이기에 누구나 접근할 수 있고, 따라서 보안성에 취약하다는 지적이 나올 수 있다. 하지만 누구나 접근이 가능하다는 것은 그만큼 보안성에 신경을 쓰는 많은 개발자들이 접근할 수 있다는 뜻이다. 따라서 많은 이들이 이에 대응하여 보안의 취약성을 파악하고 보완한다는 장점이 있다.
- 그 외에도, 리눅스는 서버 안정성, 유지보수, 호환성 등 여러 면에서 개발에 용이한 환경임이 증명되었다.

# Node JS
## Node JS는 무엇인가
- Node JS는 JavaScript 언어를 기반으로 한 런타임이다. 런타임이란 언어가 동작하는 환경이라고 생각하면 된다. 기존의 JavaScript, 이하 JS는 웹 브라우저에서 동작하도록 개발되었으나 크롬 브라우저의 V8 엔진을 통해 컴파일 할 수 있게 되었다. 따라서 기존의 프론트 엔드 분야 뿐만 아니라 서버 및 DB와 통신 등 백엔드 업무 또한 수행할 수 있게 되었다.

## NPM은 무엇인가
- Node Package Manager(NPM)은 JS 언어를 위한 패키지 관리 시스템이다. Python에서 pip 명령어와 비슷하게 node 환경에서 기타 외부 모듈을 설치할 때 `npm install` 명령어를 사용한다.

# Express
## Express는 무엇인가
- Express는 Node의 웹 프레임워크이다. node 웹 개발을 좀 더 빠르고 간결하게 수행할 수 있도록 돕는다. 공식 문서에서 라우팅, 미들웨어 등 여러가지 기능들을 소개하고 있다. (https://expressjs.com/ko/guide/routing.html)

## Express를 사용해야 하는 이유
- Express는 프레임워크이기 때문에 단순히 개발에 보조적인 역할을 한다. 따라서 Express를 사용하지 않아도 단순 node를 통해 개발이 가능하다. 하지만 서버를 열고 uri 요청에 응답하는 라우팅 코드를 작성하는데 분명한 차이가 있다.
```
// 단순 node로 서버를 열었을 때
const http = require("http");  // http는 내장모듈
const app = http.createServer((req, res) => {
    res.writeHead(200, { "Content-Type" : "text/html; charset=utf-8"});
    if (req.url === '/'){
        res.end("여기는 루트 입니다.");
    } else if (req.url === '/login'){
        res.end("여기는 로그인 화면입니다.");
    }
});

app.listen(3001, () => {
    console.log("http로 가동된 서버 입니다.");
});

```
```
// express를 사용하여 서버를 열었을 때
const express = require('express');
const app = express();

app.get("/", (req, res) => {
    res.send('여기는 루트입니다.');
});
app.get("/login", (req,res)=>{
    res.send("여기는 로그인 화면입니다.");
});
app.listen(3000, () => {
    console.log("서버 가동"); 
});
```
- node만을 사용할 경우 1. 조건문을 사용하며 2. 한글 출력에 있어서 별도로 헤더를 추가해야 한다. (line 2) 따라서 express에 비해 코드가 훨씬 길어진다. 라우팅의 경우가 많아질 경우 코드는 더욱 가독성이 떨어질 수 있다.


