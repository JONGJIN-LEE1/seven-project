# [seven-project 개발 보고서]  


프로젝트명 : seven 프로젝트  

팀명: 2팀  

작성자: 이종진  

작성일: 2025-06-19

---


# 1. 📝 프로젝트 개요

 
### 1.1 목적 

 
운동 인증 커뮤니티 서비스로, 사용자들은 본인이 원하는 그룹을 등록하거나 참여하는 등  
타인과의 공통된 취미를 공유하고, 인증하는 플랫폼 구축

 
### 1.2 주요 기능

 
- 그룹 생성,수정,삭제
- 그룹 목록 조회,상세 조회
- 그룹 추천, 추천 취소
- 그룹 참여, 참여 취소
 
- 운동 기록 등록
- 운동 기록 목록 조회
- 운동 기록 랭킹 조회
  
- 태그 목록 조회, 상세 조회
- 이미지 업로드 
---
 
# 2. ⚙️ 기술 스택 및 협업 도구
 
 
| **분류** | **사용 예정 도구** |
| :------ | :----------------- |
| Backend | Node.js 22.0.0LTS (Express) |
| Database | Prisma, PostgreSQL |
| 테스트 | Postman |
| API 문서화 | Swagger |
| 협업 도구 | Discord, GitHub ([singnyeo/nb02-seven-team2](https://github.com/singnyeo/nb02-seven-team2)), Notion ([📚 프로젝트 세부 계획](https://www.notion.so/206fca01d5c980689666cc5d59fbef08?pvs=21)) |
| 일정 관리 | GitHub Issues, Notion |
 
---
 
# 3. 📌 담당한 작업 

 
### 3.1 그룹 목록 조회

- 각 그룹의 그룹명, 닉네임, 사진, 태그, 목표 횟수, 추천수, 참여자수가 표시되며 페이지네이션이 가능
- 최신순, 추천순, 참여자순으로  정렬이 가능

---
### 3.2 그룹 상세 조회  

- 그룹명, 설명, 닉네임, 사진, 태그, 목표 횟수, 참여자 수, 디스코드 서버 초대 URL을 조회

---
### 3.3 그룹 추천, 추천 취소  

- 그룹 추천이 호출될 때마다 추천수가 1씩증가, 추천 취소 가능

---
### 3.4 운동 기록 관련 API, 이미지 업로드 API 테스트  

---  

### 3.5 테스트 계획서 및 보고서 작성

---

# 4. 📌 개발 예시  


### 4.1 그룹 목록 조회  

- API URL(POST /groups/:groupId/likes) & 요청 예시(http://localhost:3000/groups?page=1&limit=10&orderBy=createdAt&order=desc)
  
- 응답 예시 (200 OK)
 ```
 {
    "data": [
        {
            "id": 1,
            "name": "헬스마스터",
            "description": "",
            "photoUrl": "https://example.com/healthmaster.jpg",
            "goalRep": 10,
            "discordWebhookUrl": "",
            "discordInviteUrl": "",
            "likeCount": 3,
            "tags": [
                "헬스",
                "웨이트트레이닝",
                "근력운동",
                "피트니스"
            ],
            "owner": {
                "id": 1,
                "nickname": "user1",
                "createdAt": 1750066272982,
                "updatedAt": 1750066272982
            },
            "participants": [
                {
                    "id": 1,
                    "nickname": "user1",
                    "createdAt": 1750066272982,
                    "updatedAt": 1750066272982
                },
                {
                    "id": 6,
                    "nickname": "user6",
                    "createdAt": 1750066272982,
                    "updatedAt": 1750066272982
                },
                {
                    "id": 11,
                    "nickname": "user11",
                    "createdAt": 1750066272982,
                    "updatedAt": 1750066272982
                },
                {
                    "id": 16,
                    "nickname": "user16",
                    "createdAt": 1750066272982,
                    "updatedAt": 1750066272982
                }
            ],
            "createdAt": 1750066272986,
            "updatedAt": 1750066272986,
            "badges": []
        },
```
  ![그룹 목록조회](https://github.com/user-attachments/assets/c2243fb4-86f3-4f47-a794-75b8daf44b38)



### 4.2 그룹 상세 조회  

- API URL(GET  /groups/:groupId) & 요청 예시(http://localhost:3000/groups/4)
  
- 응답 예시 (200 OK)
```
{
"id": 4,
"name": "자전거여행",
"description": "자전거로 전국을 누비는 사람들",
"photoUrl": "https://example.com/bikeclub.jpg",
"goalRep": 15,
"discordWebhookUrl": "https://discord.gg/bikeclub",
"discordInviteUrl": "https://discord.gg/invitebike",
"likeCount": 2,
"tags": [
"자전거",
"사이클링",
"여행",
"아웃도어"
],
"owner": {
"id": 4,
"nickname": "user4",
"createdAt": 1750080053488,
"updatedAt": 1750080053488
},
"participants": [
{
"id": 4,
"nickname": "user4",
"createdAt": 1750080053488,
"updatedAt": 1750080053488
},
{
"id": 9,
"nickname": "user9",
"createdAt": 1750080053488,
"updatedAt": 1750080053488
},
{
"id": 14,
"nickname": "user14",
"createdAt": 1750080053488,
"updatedAt": 1750080053488
},
{
"id": 19,
"nickname": "user19",
"createdAt": 1750080053488,
"updatedAt": 1750080053488
}
],
"createdAt": 1750080053504,
"updatedAt": 1750080053504,
"badges": []
}
```
  
![그룹 상세조회](https://github.com/user-attachments/assets/6d153a26-3d24-4967-be26-5d34ca0ef667)




### 4.3 그룹 추천  

- API URL(POST /groups/:groupId/likes) & 요청 예시(http://localhost:3000/groups/6/likes)
  
- 응답 예시 (409 Conflict)

  
```
{
"success": false,
"message": "이미 추천한 그룹입니다.",
}
```

  ![그룹 추천(에러상황)](https://github.com/user-attachments/assets/c211ccc2-71a6-45ce-9a54-b422e0b4e9dd)




### 4.4 그룹 추천 취소  

- API URL(DELETE /groups/:groupId/likes) & 요청 예시(http://localhost:3000/groups/1/likes)
  
- 응답 예시 (200 OK)
  
```
{
"message": "그룹 추천을 취소했습니다."
}
```

 ![그룹 추천 취소](https://github.com/user-attachments/assets/12bc2d65-d157-48a9-b4fe-50dd17d046be)


---



# 5. 📌 운동 기록 API 테스트 예시
 
[운동 기록 API 테스트] (https://www.notion.so/API-217a1c7d0d6a808b820bda0aec5623f8)
 
[swagger 테스트] (https://www.notion.so/Swagger-API-217a1c7d0d6a80c697afe7036a4ff731)  

---  

# 6. 🗒️ 테스트 계획서 및 보고서  

[테스트 계획서] (https://www.notion.so/seven-210a1c7d0d6a80269a25f5476a37c7a3)  

[테스트 보고서] (https://www.notion.so/seven-1f9a1c7d0d6a8089bffce49da0f0520a)  

---  


# 7. 📌 문제점 및 해결 과정  

### 7.1 git pull upstream main을 진행하지 않고 로컬에서 작업하다 충돌  

: git stash를 이용하여 임시 저장하고 난 다음 git pull upstream main 진행, 
  후에 충돌 마커 확인하면서 충돌 해결  

---  

### 7.2 코딩 컨벤션 맞추는 데 어려움을 느낌(필드명 통일이나 대소문자 통합 등)  

: 데일리 스크럼 외에도 주기적으로 팀원들과 소통하며 맞추려고 노력  

---  


### 7.3 커밋을 잔뜩 쌓아두고 진행하다가 충돌이 났는데, 충돌 발견도 어려울 뿐더러 해결도 힘듦  


: 해당 PR을 닫은 후, 새로 처음부터 다시 시작  

---  


### 7.4 GroupRecommend 모델과 Participant 모델에 unique가 없어서 에러 발생  

: [@@unique([groupId, userId]) // 복합 유니크 제약 조건 추가로 에러 해결  

--- 


### 7.5 mock 데이터와 seed 데이터를 받아왔는데, seed 파일 내 경로가 mockData라 데이터를 못 받아오는 문제 발생  


: 경로를 파일명과 일치하게 mock로 변경  


```
const { GROUPS, TAGS, USERS, EXERCISE_RECORDS, GROUP_RECOMMENDS, RANKS, PHOTOS, PARTICIPANT } = require('./mockData');
```
```
const { GROUPS, TAGS, USERS, EXERCISE_RECORDS, GROUP_RECOMMENDS, RANKS, PHOTOS, PARTICIPANT } = require('./mock');
```

---  


### 7.6 swagger 테스트 중 postman과 newman 등을 이용하여 자동 테스트가 안되는 문제  

: swagger 폴더에 swagger.js(info, title 내용 들어있는 부분)와 // Swagger/OpenAPI 문서를 JavaScript 객체로 조립하는 구조 openapi.yaml(summary 내용 들어있는 부분) 이렇게 두 파일로 나눴는데, 하나의 파일로 합침

---


# 8. 📃 회고록(느낀 점)
 
### 8.1
 
본격적인 프로젝트에 앞서 schema.prisma 모델 정의 합의는 정말 중요한 것 같다. (중간에 모델 정의가 바뀌면 힘들다.)

 ---  
 
### 8.2
 
Merge 소식이 있으면(내가 하거나, 남이 하거나) 항상 git pull upstream으로 최신 상태를 유지하자. ( 최신 상태가 반영되지 않은 상태에서 작업하면 충돌이 많다.)

 ---  
 
### 8.3
 
커밋은 작은 단위로 자주 하자.( 많은 양을 한번에 커밋하려고 하다보면 코드 리뷰도 어려워지고, 충돌이 났을 때 고치기도 힘들다.)

 ---  
 
### 8.4 
 
의존성 같은 개발 환경은 처음에 다 같이 맞추고 들어가는 게 편하다. 폴더 구조도.

 ---  
 
### 8.5
 
백엔드에서 API 개발 후 postman 같은 도구들을 활용해서 응답이 잘 되는지 확인하는 테스트가 성공하더라도, 프론트엔드와 연동했을 때 오류가 날 수 있다. 
(jest:단위테스트 하는 법은 아직 배우지 않아서 postman만 활용. 프론트엔드와 연동했을 때 오류가 나는 건 각각의 서버 터미널을 보면 어디 오류인지 확인할 수 있다.
예를 들어 백엔드 서버에서는 정상적으로 200 OK 응답 신호를 보냈는데, 프론트엔드 서버에서는 오류가 난다거나 하는 식으로. 이럴 경우 프론트엔드 코드를 고쳐야 하는데, 프론트엔드를 배우지 못했다보니 어찌해야 할지 난감하다. 그렇다고 백엔드 코드를 프론트엔드 코드에 맞게 수정하자니 백엔드 코드들은 잘 응답이 되었다는 점,  프론트엔드 폴더의 어느 부분을 참고해서 고쳐야 할 지 막막하다는 점이 힘든 것 같다.)

 ---  
 
### 8.6
 
커밋과 푸시는 신중히 ! (나중에 되돌리고 싶은 경우가 생기는데, 이 경우 상당히 복잡하다. git commit —amend를 쓰거나 git reset —soft HEAD~1, git revert <커밋해시> 등)

 ---  
 
### 8.7
 
PR 때 No conflicts with base branch라고 떠서 안심하고 Merge해도 나중에 오류가 날 수 있다.

---  

### 8.8
 
팀원들과의 소통이 굉장히 중요하다.

---  
 
### 8.9
 
공통으로 자주 쓰이는 함수나 변수 같은 경우는 utils 폴더를 만들어서 꺼내 쓰는 방법이 좋을 수 있다.

---  

### 8.10
 
PR을 날린 상황에서, 변경 사항이 생기면 PR을 닫지 않은 상태로도 커밋, 푸시하면 기록이 남는다.(여태 PR을 닫고 다시 새 PR을 날렸는데, 헛고생했다.)

---  

### 8.11
 
확인 작업은 차근차근 ! 
 
스키마 모델과 일치하는지
 
요구 사항과 부합하는지
 
API 명세서와 일치하는지
 
프론트엔드 코드들과 충돌은 일어나지 않는지

---  

### 8.12
 
swagger를 postman과 newman으로 자동 테스트를 진행하려면 전체 OpenAPI 문서를 하나의 파일로 합쳐야한다는 사실.
프로젝트 구조를 swagger 폴더에 swagger.js(info, title 내용 들어있는 부분) // Swagger/OpenAPI 문서를 JavaScript 객체로 조립하는 구조, openapi.yaml(summary 내용 들어있는 부분) 이렇게 두 파일로 나눴는데, 이렇게 나눠져있으면 Postman에서 못 읽는다.

---




