# Setting Up Your Database

## Create a Postgres database

vercel.com 에서
Storage 탭에서 .env.local 탭으로 이동하여 "Show secret"을 클릭하고 스니펫을 복사하십시오. 복사하기 전에 비밀 정보를 반드시 표시하십시오.

코드 편집기로 이동하여 .env.example 파일의 이름을 .env로 변경하십시오. Vercel에서 복사한 내용을 붙여넣으십시오.

중요: .gitignore 파일로 이동하여 .env가 무시되는 파일 목록에 포함되어 있는지 확인하십시오. 이렇게 하면 데이터베이스 비밀 정보가 GitHub에 푸시될 때 노출되는 것을 방지할 수 있습니다.

마지막으로, 터미널에서 npm i @vercel/postgres 명령어를 실행하여 Vercel Postgres SDK를 설치하십시오.

## Seed your database

이제 데이터베이스가 생성되었으니 일부 초기 데이터로 시드(seed)를 만들어 보겠습니다. 이를 통해 대시보드를 구축하는 동안 사용할 데이터를 얻을 수 있습니다.

프로젝트의 /scripts 폴더에는 seed.js라는 파일이 있습니다. 이 스크립트에는 송장(invoices), 고객(customers), 사용자(user), 수익(revenue) 테이블을 생성하고 씨드 데이터로 채우는 지시사항이 포함되어 있습니다.

코드의 모든 내용을 이해하지 못해도 걱정하지 마세요. 코드는 SQL을 사용하여 테이블을 생성하고 생성된 후 placeholder-data.js 파일의 데이터를 채웁니다.

다음으로, package.json 파일에 다음 줄을 스크립트에 추가하십시오:

// package.json

"scripts": {
  "build": "next build",
  "dev": "next dev",
  "start": "next start",
  "seed": "node -r dotenv/config ./scripts/seed.js"
},

이제 npm run seed를 실행하십시오. 스크립트가 실행되고 있음을 알려주는 몇 가지 console.log 메시지가 터미널에 표시될 것입니다.
