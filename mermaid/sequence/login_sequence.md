sequenceDiagram
  actor A1 as 使用者
  participant Frontend as Frontend
  participant OAuthProvider as Google/Microsoft OAuth
  participant Backend as Backend
  participant Database as Database

  A1 ->> Frontend: 點擊「Google/Microsoft 登入」
  Frontend ->> OAuthProvider: Redirect 授權請求（含 client_id、redirect_uri、scope）
  OAuthProvider -->> Frontend: Redirect 至 redirect_uri（附帶 code）
  Frontend ->> Backend: POST /api/system/auth/login/（附帶 code、type）
  Backend ->> OAuthProvider: 用 code 換取 access_token / id_token
  OAuthProvider -->> Backend: 回傳 access_token + 使用者資訊
  Backend ->> Database: 查詢 / 建立使用者（依 email / sub）
  Database -->> Backend: 回傳使用者資料
  Backend -->> Frontend: 回傳 JWT token（含 access_token、refresh_token）
  Frontend -->> A1: 儲存 token 並導向首頁
