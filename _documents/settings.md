## Flask-Graphql server

- [1. 파이썬과 플라스크로 기본적인 GraphQL 서버 만들어보기 // GraphQL with Flask(Python)](https://lewisxyz000.tistory.com/30)
- [Build a GraphQL API with Python, Flask and Ariadne](https://www.twilio.com/blog/graphql-api-python-flask-ariadne)
- [GraphQL 무작정 시작하기 (1) - Schema & Query](https://heodolf.tistory.com/109)

### Mongodb 설치

- [Mongodb설치하고 환경변수 설정하기(ver 4.2.0)](https://somjang.tistory.com/entry/WindowsMongodb%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0ver-420)

#### MongoDB 다운로드
- [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
- mongodb-windows-x86_64-4.4.3-signed.msi

#### msi 실행
- 'complete' 설치
- Install MongoDB Compass 체크 해제

#### 환경변수 설정
- 시스템 환경 변수 편집 > 환경 변수 > 시스템 변수 > path > 편집 > 새로 만들기
- C:\Program Files\MongoDB\Server\4.4\bin

#### dbpath 설정
```
cd C:\Dev\docMoon
mkdir _database
cd _database
mkdir mongo
```

#### 서버/클라이언트 실행
- mongo server 시작
```
mongod --dbpath=C:/Dev/docMoon/_database/mongo
```

- mongo 클라이언트 실행
```
mongo
```


### github 세팅

#### remote 저장소 생성
remote: https://github.com/moonitdev/FGS.git

#### local 저장소 생성
local: C:\Dev\docMoon\projects> git clone https://github.com/moonitdev/FGS.git


### python 패키지 설치

#### conda 가상환경 생성
```
C:\Dev\docMoon\projects\FGS>conda create -n fgs flask
```

#### pip 설치
```
C:\Dev\docMoon\projects\FGS>conda activate fgs
(fgs) C:\Dev\docMoon\projects\FGS> pip install python-dotenv flask-graphql graphene graphene-mongo mongoengine mongomock

```


### test app
- [GraphQL 무작정 시작하기 (1) - Schema & Query](https://heodolf.tistory.com/109)

#### 파일 생성/편집
- app.py
- .env
- api/__init__.py
- api/database.py
- api/models.py
- api/schema.py

#### flask server 실행
```
(fgs) C:\Dev\docMoon\projects\FGS>python app.py
```

#### graphql 확인
- 브라우저 실행 > http://localhost:3000/graphql 접속
- 오른쪽 상단 'Docs' 클릭 > Schema 정보 확인

```query
# 전체 랭킹 조회                                                        
query {
  ranks {
    mode
    name
    score
    isMobile
    regDttm
  }
}
```

```
# 4x4 모드의 랭킹 조회                                                        
query {
  ranksForMode(mode: "4x4") {
    id
    mode
    name
    score
    isMobile
    regDttm
  }
}
```

```
# 특정 랭킹의 정보 조회                                                             
query {
  rank(id: "60212fc377c272d43713644d") {
    id
    mode
    name
    score
    isMobile
    regDttm
  }
}
```

