# InRockLife-Backend-Doc
揪團後台API

***
## ManagerLogin - 管理員登入
```
URL：api/backend/ManagerLogin.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  ManagerAccount(string)：管理員帳號
  ManagerPassword(string)：管理員密碼
傳入範例：
  data={"ManagerAccount":"xxx","ManagerPassword":"xxx"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    ManagerId(string)：管理員 (唯一碼)
    AuthToken(string)：身分驗證令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerId":"1","AuthToken":"1bab341c06ca0d432e3d37adc892a4a1"}}
失敗範例：
  {"status":1101,"msg":"無此帳號","data":{}}
  {"status":1102,"msg":"密碼錯誤","data":{}}
  {"status":1103,"msg":"無權限","data":{}}
```

## ManagerLogout - 管理員登出
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/backend/ManagerLogout.php
MetHod：GET
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  參考共用錯誤代碼
```

## Modify - 修改拼圖機率
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```
