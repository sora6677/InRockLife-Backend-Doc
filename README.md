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

## OfficialList - 官方任務列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/backend/OfficialList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍: 10 ~ 100
  GetPage(int)：第幾頁 範圍: > 1
傳入範例：
  data={"RowCount":10,"GetPage":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    TotalPage(int)：總頁數
    TotalRows(int)：總筆數
    OfficialList(object array)：官方任務列表
      OfficialId(int)：官方任務ID
      OfficialName(string)：任務名稱
      StartDateTime(string)：任務開始時間
      EndDateTime(string)：任務結束時間
      IsDisplay(int)：APP是否顯示 0:不顯示 1:顯示
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalRows":1,"OfficialList":[{"OfficialId":1,"OfficialName":"海線美食大冒險","StartDateTime":"2023-01-12 00:00:00","EndDateTime":"2023-02-01 00:00:00","IsDisplay":1}]}}
失敗範例：
  參考共用錯誤代碼
```

## OfficialModify - 官方任務修改
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/backend/OfficialModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  OfficialName(string)：任務名稱
  StartDateTime(string)：任務起始時間
  EndDateTime(string)：任務結束時間
  IsDisplay(int)：APP是否顯示 0:不顯示 1:顯示
傳入範例：
  data={"OfficialId":1,"OfficialName":"海線美食大冒險","StartDateTime":"2023-01-12 00:00:00","EndDateTime":"2023-02-01 00:00:00","IsDisplay":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  參考共用錯誤代碼
```

## PuzzleDataGet - 拼圖資料取得
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/backend/PuzzleDataModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PuzzleId(int)：拼圖ID
  PuzzleProbability(int)：拼圖機率(%) EX: 10 = 10%
傳入範例：
  data={"PuzzleId":1,"PuzzleProbability":1}
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

## PuzzleDataModify - 拼圖資料修改
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/backend/PuzzleDataModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PuzzleId(int)：拼圖ID
  PuzzleProbability(int)：拼圖機率(%) EX: 10 = 10%
傳入範例：
  data={"PuzzleId":1,"PuzzleProbability":1}
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
