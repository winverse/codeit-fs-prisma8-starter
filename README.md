# codeit-fs-prisma8-starter

`32. Prisma 8 배워보기` 토픽의 시작 상태를 담은 저장소입니다.

## 프로젝트 목적

Prisma 8과 Express로 사용자 정보를 생성·조회·수정·삭제하는 JavaScript API를 만듭니다. 완성하면 다음 요청이 동작합니다.

| 메서드 | 경로 | 동작 |
| --- | --- | --- |
| `POST` | `/users` | 사용자를 추가합니다. 이메일이 중복되면 `409`로 응답합니다. |
| `GET` | `/users` | 사용자 목록을 `id`, `email`, `name`만 담아 응답합니다. |
| `GET` | `/users/:id` | 사용자 한 명을 응답합니다. 없으면 `404`로 응답합니다. |
| `PATCH` | `/users/:id` | 사용자 이름을 수정합니다. 없으면 `404`로 응답합니다. |
| `DELETE` | `/users/:id` | 사용자를 삭제하고 `204`로 응답합니다. 없으면 `404`로 응답합니다. |

## 진행 방식

이 토픽은 빈 폴더에서 Prisma 8 프로젝트를 만드는 과정부터 배웁니다. 따라서 수업에서는 이 저장소를 내려받지 않고, 교재의 `2장 01. 프로젝트 생성과 Prisma CLI 설치`부터 새 폴더에서 따라 합니다. 이 저장소는 수업을 시작하기 전의 빈 상태를 보존하며, 제공하는 애플리케이션 코드는 없습니다.

## 시작 명령

```bash
mkdir prisma8-users
cd prisma8-users
pnpm init
pnpm add -D prisma
```

이어지는 설치, 초기화, 파일 작성 순서는 교재를 따릅니다.

## 직접 만들거나 수정하는 파일

| 파일 | 내용 |
| --- | --- |
| `prisma.config.js` | Prisma CLI 설정 |
| `src/prisma/contract.prisma` | 초기화 명령이 만든 데이터 계약에서 `User` 모델만 남긴 파일 |
| `src/prisma/db.js` | 쿼리를 실행할 `db` 객체 |
| `src/app.js` | Express 서버와 CRUD 라우트 |

## 실행 확인

교재를 마치면 `pnpm dev`로 서버를 실행하고, 터미널에 `서버가 http://localhost:3000 에서 실행 중입니다.`가 표시됩니다. `GET http://localhost:3000/users` 요청으로 사용자 목록을 확인합니다.
