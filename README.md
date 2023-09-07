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

**Query, Mutation 사용구분**

User가 데이터를 받아오게 하고싶다면 *Query* 안에 있어야하고
User가 데이터를 보내서 업데이트, 삭제를 하려면 *Mutation*이 되어야 한다.

```javascript
    type Query{
        allTweets: [Tweet]
        tweet(id:ID): Tweet
    }
    type Mutation{
        postTweet(text:String, userId: ID): Tweet
        deleteTweet(id:ID): Boolean
    }
```