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

**!의 활용**

```javascript
type Query{
        allTweets: [Tweet!]!
        tweet(id:ID!): Tweet
    }
```
!는 어떤 값이 required 라고 지정해주는 것을 의미한다.
tweet(id:ID!) 처럼 argumnent를 required로 설정할 수 있고
allTweets: [Tweet!]! 의 경우엔 []!는 allTweets이 반드시 [];list 값을 가져야 하며,
[]안의 값은 언제나 [Tweet!] 값이어야 한다는 의미다. DB에 Tweet이 없을 경우 (서버가 막 시작했거나)값이 없는 경우가 가능하지만 null 값이 나올순 없다.
이렇게 nullable, non-nullable은 매우 중요하다. 
"tweet(id:ID!): Tweet" 에서 id:ID!는 값이 없을 수 있다. 그래서 출력값 Tweet은 nullable값으로 표현된다. 

**resolver 함수 args의 순서**
```javascript
ex, IQOS(root, args)
```

* DB를 mutate한다면, 함수를 Mutation에 작성하고
  그저 data를 fetching하는거라면 Query에 작성한다.