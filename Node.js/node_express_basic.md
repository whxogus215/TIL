# Node JS

## 목차
0. [Git bash 명령어 정리](#Git-bash-명령어-정리)
    - [리눅스 명령어를 사용하는 이유](#리눅스를-왜-사용해야-할까)
1. [Node JS](#node-js는-무엇인가)
    - [NPM](#npm은-무엇인가)
    - [Package.json](#packagejson)

2. [Express](#express는-무엇인가)
    - [Express를 사용해야 하는 이유](#express를-사용해야-하는-이유)

3. [JavaScript](#javascript)
    - [fetch](#fetch)


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

## Package.json
- Package.json 파일은 npm init을 하거나 express를 설치할 때 설정하는 패키지 관리 파일이다. 이 파일은 JSON 타입으로 되어 있으며, 해당 프로젝트에 필요한 모듈 및 버전 등이 명시되어 있다.
- 파일의 scripts 란에 명령어 단축키를 저장할 수 있다.
### node_modules을 깃허브에 올리지 않는 이유
- 기본적으로 깃이나 깃허브에 커밋할 때 node_modules를 포함하지 않는다. node_modules에는 node에 필요한 모든 모듈들이 담겨 있으며, 특정 프로젝트에 불필요한 모듈도 분명히 있을 것이다. **즉, 우리가 필요한 모듈만 설치하기 위해서 Package.json을 참조하면 된다.** Package.json에는 설치한 모듈들이 작성되어 있으며("dependencies"), 이 파일만 있으면 터미널에 `npm init`만 치면 알아서 dependencies의 모듈이 자동으로 설치된다. 따라서 node_modules 별도로 설치하지 않아도 된다.
### Package-lock.json이란?
- Package-lock.json도 기본적으로 Package.json가 유사하지만 모듈에 대한 버전 정보가 좀 더 명확하고 자세하게 명시되어 있다.
- Package.json의 경우 버전의 내용이 "^3.1.8" 이런식으로 범위로 지정되어 있고, Package-lock.json의 경우 해당 모듈의 버전이 정확이 몇 버전인지 나와있다.
- 버전 표기 방법
    1. ^3.1.5 (캐럿) : 두번째 소수자리의 영역을 표시\
    ex) 3.2.5, 3.3.5는 허용, 4.1.5, 5.1.5는 허용하지 않음.
    2. ~3.1.5 : 세번째 소수자리의 영역을 표시\
    ex) 3.1.6, 3.1.8 허용
    3. 3.1.x : x에 해당하는 모든 값을 허용
    ex) 더 낮은 버전이어도 x에 해당하는 부분이면 상관없음.
















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



# JavaScript
## fetch
- 자바스크립트는 웹 페이지를 제어하는 언어이다. DOM을 통해 웹 페이지의 구성 요소를 제어할 수 있는 권한이 있다. 우리가 사용하는 `querySelector` 등도 document의 객체이다. 홈페이지에서 서버로 요청하는 데이터를 처리하기 위해서는 해당 페이지와 연결된 js 파일에서 처리하는 함수를 만들어주어야 한다. 이 때 사용하는 기능이 fetch이다.
- 
```
// 프론트에서 서버로 데이터를 보내는 방법 fetch
    fetch("/login", {
        // 서버로 보내는 데이터
        method : "POST",
        headers : {
            "Content-Type" : "application/json"
        },
        body: JSON.stringify(req)
    })
```
위와 같이 특정 uri에 접근했을 때 api로 어떤 정보들을 전달할 지에 대해 명시한다. 위 코드는 POST 요청이며, 헤더에 해당 데이터가 어떤 타입인지(JSON), 그리고 요청의 바디 부분에 해당하는 데이터(오브젝트)를 문자열 형태로 전달한다.



