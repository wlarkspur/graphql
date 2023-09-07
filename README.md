# GraphQL Setup

**Setup**

1. cmd 실행
2. mkdir abc : 폴더 생성
3. code abc : vscode로 해당 파일 실행
4. npm init -y : 시작
5. npm i ... 필요 패키지 설치

**Tip**

package.json 에 module 타입 설정하면 (script안에 "dev" 변경해준다. )
```javascript
{
  "scripts": {
    "dev": "nodemon server.js"
  },  
  "type":"module"
  
}
```
---
아래 import xxx from xxx 명령어를 사용할 수 있게 된다.
```javascript
import { ApolloServer, gql } from "apollo-server"; 
const {ApolloServer, gql} =require("apollo-server")
```

이후 npm run dev을 실행하면 javascript server실행이 가능하다.

**Comparison**

REST API vs GraphQL 

```javascript

GET /text

const typeDefs = gql`

    type Query{
        text: String
    }

`
```