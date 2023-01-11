# InRockLife-Backend-Doc
揪團後台API

***
## ManagerLogin - 管理員登入
```
URL：api/manager/ManagerLogin.php
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
    ManagerId(string)：管理員ID
    ManagerToken(string)：管理員令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerId":"1","AuthToken":"1bab341c06ca0d432e3d37adc892a4a1"}}
失敗範例：
  {"status":1101,"msg":"登入失敗","data":{}}
  {"status":1102,"msg":"密碼錯誤","data":{}}
```

## Modify - 修改拼圖機率
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```
