# codeit-fs-prisma8-starter

`32. Prisma 8 배워보기` 토픽의 시작 상태를 담은 저장소입니다.

## 프로젝트 목적

Prisma 8과 Express로 사용자와 사용자가 쓴 글을 다루는 JavaScript API를 만듭니다. 완성하면 다음 요청이 동작합니다.

| 메서드 | 경로 | 동작 |
| --- | --- | --- |
| `POST` | `/users` | 사용자를 추가합니다. 요청 본문의 `posts` 배열로 그 사용자의 글도 함께 추가하며, 이메일이 중복되면 `409`로 응답합니다. |
| `GET` | `/users` | 사용자 목록을 `id`, `email`, `name`만 담아 최근에 추가한 순서로 응답합니다. `search`로 이름을 검색하고 `page`, `limit`으로 페이지를 나눕니다. |
| `GET` | `/users/:id` | 사용자 한 명을 응답합니다. 없으면 `404`로 응답합니다. |
| `PATCH` | `/users/:id` | 사용자 이름을 수정합니다. 없으면 `404`로 응답합니다. |
| `DELETE` | `/users/:id` | 사용자를 삭제하고 `204`로 응답합니다. 없으면 `404`로 응답합니다. |
| `GET` | `/users/:id/posts` | 사용자와 그 사용자가 쓴 글을 함께 응답합니다. 없으면 `404`로 응답합니다. |
| `GET` | `/authors` | 공개 글이 있는 사용자를 공개 글과 함께 응답합니다. |

## 진행 방식

이 토픽은 빈 폴더에서 Prisma 8 프로젝트를 만드는 과정부터 배웁니다. 따라서 수업에서는 이 저장소를 내려받지 않고, 교재의 `2장 01. 프로젝트 생성과 Prisma CLI 설치`부터 새 폴더에서 따라 합니다. 이 저장소는 수업을 시작하기 전의 빈 상태를 보존하며, 제공하는 애플리케이션 코드는 없습니다.

## 시작 명령

```bash
mkdir prisma-user-api
cd prisma-user-api
pnpm init
pnpm add -D prisma
```

이어지는 패키지 설치, 파일 작성, 데이터베이스 반영 순서는 교재를 따릅니다.

## 직접 만들거나 수정하는 파일

| 순서 | 파일 | 내용 |
| --- | --- | --- |
| 1 | `src/prisma/contract.prisma` | `User`와 `Post` 모델, 두 모델의 관계를 담은 데이터 계약 |
| 2 | `prisma.config.js` | Prisma CLI 설정(계약 위치, 데이터베이스 연결 주소) |
| 3 | `package.json` | 계약 emit, 데이터베이스 반영, 서버 실행 스크립트 |
| 4 | `.env` | 데이터베이스 연결 주소 |
| 5 | `src/prisma/db.js` | 쿼리를 실행할 `db` 객체 |
| 6 | `src/app.js` | Express 서버와 사용자·글 라우트 |

## 실행 확인

교재를 마치면 `pnpm dev`로 서버를 실행하고, 터미널에 `서버가 http://localhost:3000 에서 실행 중입니다.`가 표시됩니다. `GET http://localhost:3000/users` 요청으로 사용자 목록을 확인합니다.
