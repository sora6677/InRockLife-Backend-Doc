# InRockLife-Backend-Doc
揪團後台API

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|資料異常|
|1002|連線異常|
|1003|令牌失效|
|1004|未上傳圖檔|
|1005|上傳圖檔失敗|
|1006|查無資料|

***
## ManagerLogin - 管理員登入
```
URL：api/inrocklife/backend/manager/ManagerLogin.php
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
URL：api/inrocklife/backend/manager/ManagerLogout.php
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

***

## GetAnnouncementList - 公告列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/information/GetAnnouncementList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍: 10 ~ 100
  GetPage(int)：第幾頁 範圍: > 0
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
    AnnouncementList(object array)：公告列表
      AnnouncementId(int)：公告ID
      AnnouncementCover(string)：公告封面網址
      AnnouncementLink(string)：公告超連結
      StartDateTime(string)：公告顯示時間
      EndDateTime(string)：公告消失時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalRows":1,"AnnouncementList":[{"AnnouncementId":1,"AnnouncementCover":"http:\/\/img.inrocklife.net\/images\/announcement\/2023\/01\/30\/announcement_list\/802801302254502023.mp4","AnnouncementLink":"https:\/\/www.youtube.com\/","StartDateTime":"2023-01-31 00:00:00","EndDateTime":"2023-02-28 00:00:00"}]}}
失敗範例：
  參考共用錯誤代碼
```

## CreateAnnouncement - 建立公告
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/information/CreateAnnouncement.php
MetHod：POST
傳入參數：
  data：JSON
  AnnouncementFile(FILE)： 公告圖片或影片, 上傳檔案
傳入JSON：
  AnnouncementLink(string)：公告超連結
  StartDateTime(string)：公告顯示時間
  EndDateTime(string)：公告消失時間
傳入範例：
  data={"AnnouncementLink":"https://www.youtube.com/","StartDateTime":"2023-01-31 00:00:00","EndDateTime":"2023-02-27 00:00:00"}
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

## UpdateAnnouncement - 更新公告
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/information/UpdateAnnouncement.php
MetHod：POST
傳入參數：
  data：JSON
  AnnouncementFile(FILE)： 公告圖片或影片, 上傳檔案 **非必填
傳入JSON：
  AnnouncementId(int)：公告ID
  AnnouncementLink(string)：公告超連結
  StartDateTime(string)：公告顯示時間
  EndDateTime(string)：公告消失時間
傳入範例：
  data={"AnnouncementId":1,"AnnouncementLink":"https://www.youtube.com/","StartDateTime":"2023-01-31 00:00:00","EndDateTime":"2023-02-28 00:00:00"}
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

## DeleteAnnouncement - 刪除公告
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/information/DeleteAnnouncement.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  AnnouncementId(int)：公告ID
傳入範例：
  data={"AnnouncementId":1}
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

***
## LotteryWinList - 中獎列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/statistical/LotteryWinList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍: 10 ~ 100
  GetPage(int)：第幾頁 範圍: > 0
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
    WinList(object array)：中獎名單
      UserPhone(int)：玩家手機
      UserNickName(string)：玩家暱稱
      PrizeName(string)：獎品名稱
      PrizeQuota(int)：獎品名額
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalRows":2,"WinList":[{"UserPhone":"0911234521","UserNickName":"系浮方","PrizeName":"iPhone 14手機","PrizeQuota":1},{"UserPhone":"0911234521","UserNickName":"系浮方","PrizeName":"浮現祭老帽-黑色","PrizeQuota":1}]}}
失敗範例：
  參考共用錯誤代碼
```

***
## TaskTypeList - 任務類型列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/TaskTypeList.php
MetHod：GET
```

```
回傳方式：JSON
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    TypeList(object array)：類型列表 ***類型與前台 APP 配合，目前僅有 6 項
      TaskType(int)：類型ID
      TaskName(string)：類型名稱
      IsDisplay(int)：前台 APP 是否顯示 0:不顯示 1:顯示
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TypeList":[{"TaskType":1,"TaskName":"揪運動","IsDisplay":0},{"TaskType":2,"TaskName":"揪一起","IsDisplay":1},{"TaskType":3,"TaskName":"揪活動","IsDisplay":0},{"TaskType":4,"TaskName":"揪吃飯","IsDisplay":0},{"TaskType":5,"TaskName":"揪玩樂","IsDisplay":0},{"TaskType":6,"TaskName":"揪蝦拚","IsDisplay":0}]}}
失敗範例：
  參考共用錯誤代碼
```

## TaskTypeInsert - 新增任務類型
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/TaskTypeInsert.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  TypeList(object array)：
      TaskType(int)：類型ID
      TaskName(string)：類型名稱
      IsDisplay(int)：前台 APP 是否顯示 0:不顯示 1:顯示
傳入範例：
  data={"TaskType":2,"TaskName":"揪一起","IsDisplay":1}
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
  參考共用錯誤代碼 或
  {"status":1111,"msg":"類型已存在","data":{}}
```

## TaskTypeModify - 修改任務類型
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/TaskTypeModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  TypeList(object array)：
      TaskType(int)：類型ID **此欄為識別用，不可更改
      TaskName(string)：類型名稱
      IsDisplay(int)：前台 APP 是否顯示 0:不顯示 1:顯示
傳入範例：
  data={"TaskType":2,"TaskName":"揪一起","IsDisplay":0}
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
  參考共用錯誤代碼 或
  {"status":1110,"msg":"無此類型","data":{}}
```

***
## TaskTypeDelete - 刪除任務類型
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/TaskTypeDelete.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  TypeList(object array)：
      TaskType(int)：類型ID **此欄為識別用，不可更改
      TaskName(string)：類型名稱
      IsDisplay(int)：前台 APP 是否顯示 0:不顯示 1:顯示
傳入範例：
  data={"TaskType":7}
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
  參考共用錯誤代碼 或
  {"status":1110,"msg":"無此類型","data":{}}
```

## GetModeList - 可選模式列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/GetModeList.php
MetHod：GET
```

```
回傳方式：JSON
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    ModeList(object array)：模式列表
      TaskMode(int)：任務模式(唯一碼)
      ModeName(string)：模式名稱
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ModeList":[{"TaskMode":1,"ModeName":"寶箱模式"}]}}
失敗範例：
  參考共用錯誤代碼
```

## GraphicsList - 圖形列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/GraphicsList.php
MetHod：GET
```

```
回傳方式：JSON
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    ModeList(object array)：模式列表
      GraphicsId(int)：圖形ID
      GraphicsName(string)：圖形名稱
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"GraphicsList":[{"GraphicsId":1,"GraphicsName":"美食大冒險圖形A"},{"GraphicsId":2,"GraphicsName":"美食大冒險圖形B"},{"GraphicsId":3,"GraphicsName":"美食大冒險圖形C"}]}}
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
URL：api/inrocklife/backend/task/OfficialList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍: 10 ~ 100
  GetPage(int)：第幾頁 範圍: > 0
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
      ModeName(string)：模式名稱
      OfficialDescribe(string)：任務描述
      StartDateTime(string)：任務開始時間
      EndDateTime(string)：任務結束時間
      IsDisplay(int)：APP是否顯示 0:不顯示 1:顯示
      TotalPuzzles(int)：綁定的拼圖總數
      MinPeople(int)：最少人數
      MaxPeople(int)：最大人數
      GraphicsList(int array)：綁定圖形ID列表，圖形可複選 **參照 GraphicsList - 圖形列表
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalRows":1,"OfficialList":[{"OfficialId":1,"OfficialName":"海線美食大冒險","ModeName":"寶箱模式","OfficialDescribe":"描述","StartDateTime":"2023-01-12 00:00:00","EndDateTime":"2023-02-01 00:00:00","IsDisplay":1,"TotalPuzzles":60,"MinPeople":1,"MaxPeople":3,"GraphicsList":[1,2,3]}]}}
失敗範例：
  參考共用錯誤代碼
```

## OfficialCreate - 官方任務建立
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/OfficialCreate.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  TaskMode(int)：任務模式，僅創建時可選 **參照 GetModeList - 可選模式列表
  OfficialName(string)：任務名稱 **不可為空,最長 20 個字
  OfficialDescribe(string)：任務描述 **最長 200 個字
  StartDateTime(string)：任務起始時間 **格式: yyyy-mm-dd hh:ii:ss (24小時制)
  EndDateTime(string)：任務結束時間 **格式: yyyy-mm-dd hh:ii:ss (24小時制)
  IsDisplay(int)：APP是否顯示 0:不顯示 1:顯示
  MinPeople(int)：最少人數
  MaxPeople(int)：最大人數
  GraphicsList(int array)：綁定圖形ID列表，圖形可複選 **參照 GraphicsList - 圖形列表
傳入範例：
  data={"TaskMode":1,"OfficialName":"海線美食大冒險","OfficialDescribe":"寶箱活動","StartDateTime":"2023-02-09 00:00:00","EndDateTime":"2023-02-28 00:00:00","IsDisplay":1,"MinPeople":1,"MaxPeople":3,"GraphicsList":[1,2,3]}
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
  {"status":1020,"msg":"名稱或內容長度不符","data":{}}
  {"status":1107,"msg":"超過拼圖總數","data":{}}
```

## OfficialModify - 官方任務修改
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/OfficialModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  OfficialName(string)：任務名稱 **不可為空,最長 20 個字
  OfficialDescribe(string)：任務描述 **最長 200 個字
  StartDateTime(string)：任務起始時間 **格式: yyyy-mm-dd hh:ii:ss (24小時制)
  EndDateTime(string)：任務結束時間 **格式: yyyy-mm-dd hh:ii:ss (24小時制)
  IsDisplay(int)：APP是否顯示 0:不顯示 1:顯示
  MinPeople(int)：最少人數
  MaxPeople(int)：最大人數
  GraphicsList(int array)：綁定圖形ID列表，圖形可複選 **參照 GraphicsList - 圖形列表
傳入範例：
  data={"OfficialId":1,"TaskMode":1,"OfficialName":"海線美食大冒險","OfficialDescribe":"描述","StartDateTime":"2023-01-12 00:00:00","EndDateTime":"2023-02-01 00:00:00","IsDisplay":1,"MinPeople":1,"MaxPeople":3,"GraphicsList":[1,2,3]}
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
  {"status":1020,"msg":"名稱或內容長度不符","data":{}}
  {"status":1107,"msg":"超過拼圖總數","data":{}}
```

## BoxContentSetting - 寶箱內容設定
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxContentSetting.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
傳入範例：
  data={"OfficialId":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    ContentId(int)：獎項ID ** 1:幣,2:拼圖,3:徽章
    ContentDescribe(string)：獎項描述
    SettingMethodList(object array)：可設定的方法 1:範圍取值 2:設定數值開出機率 3:指定數值均出現,則設定數值有機率開出 4:設定數值未出現,則有機率開出
      SettingMethod(int)：設定方法
      SettingDescribe(string)：方法描述
      SettingFields(string array)：所需欄位
      SettingFieldsType(string array)：欄位型別
      SettingFieldsDescribe(string array)：欄位描述
    AwardFields(string array)：所需欄位
    AwardFieldsType(string)：欄位型別
    AwardFieldsDescribe(string)：欄位描述
    AwardFieldsComment(string)：欄位註解說明
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"ContentId":1,"ContentDescribe":"水晶碎片(數量)","SettingMethodList":[{"SettingMethod":1,"SettingDescribe":"範圍取值","SettingFields":["MinQuantity","MaxQuantity"],"SettingFieldsType":["int","int"],"SettingFieldsDescribe":["最小數量","最大數量"]}],"AwardFields":["AwardProbability"],"AwardFieldsType":["int"],"AwardFieldsDescribe":["獎項機率"],"AwardFieldsComment":["所有獎項總機率不可超過 100,獎項機率可填0，若都填0表示隨機"]},{"ContentId":2,"ContentDescribe":"拼圖(機率)","SettingMethodList":[{"SettingMethod":2,"SettingDescribe":"設定ID機率","SettingFields":["SettingValues","Probability"],"SettingFieldsType":["string","int"],"SettingFieldsDescribe":["拼圖(ID)*可傳入多個,以逗號(,)區分","開出機率"]},{"SettingMethod":3,"SettingDescribe":"指定的ID均出現,則某ID有機率開出","SettingFields":["SettingValue","SpecifiedValues","Probability"],"SettingFieldsType":["string","string","int"],"SettingFieldsDescribe":["某拼圖(ID)","指定的拼圖(ID)*可傳入多個,以逗號(,)區分","開出機率"]},{"SettingMethod":4,"SettingDescribe":"ID未出現,則依機率開出","SettingFields":["SettingValue","Probability"],"SettingFieldsType":["string","int"],"SettingFieldsDescribe":["拼圖(ID)","開出機率"]}],"AwardFields":["AwardProbability"],"AwardFieldsType":["int"],"AwardFieldsDescribe":["獎項機率"],"AwardFieldsComment":["所有獎項總機率不可超過 100,獎項機率可填0，若都填0表示隨機"]},{"ContentId":3,"ContentDescribe":"徽章(數量)","SettingMethodList":[{"SettingMethod":1,"SettingDescribe":"範圍取值","SettingFields":["MinQuantity","MaxQuantity"],"SettingFieldsType":["int","int"],"SettingFieldsDescribe":["最小數量","最大數量"]}],"AwardFields":["AwardProbability"],"AwardFieldsType":["int"],"AwardFieldsDescribe":["獎項機率"],"AwardFieldsComment":["所有獎項總機率不可超過 100,獎項機率可填0，若都填0表示隨機"]}]}
失敗範例：
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
```

## BoxTemplateList - 寶箱樣板列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxTemplateList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
傳入範例：
  data={"OfficialId":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    TemplateId(int)：寶箱樣板ID
    TemplateName(string)：樣板名稱
    BoxCoolDownTime(int)：冷卻時間 (分鐘)
    BoxStartDateTime(string)：出現時間
    BoxEndDateTime(string)：消失時間
    BoxContents(object array)：參照 BoxContentSetting API
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"BoxTemplateList":[{"TemplateId":1,"TemplateName":"樣版名稱1","BoxCoolDownTime":5,"BoxStartDateTime":"2023-02-16 00:00:00","BoxEndDateTime":"2023-02-28 00:00:00","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10}],"AwardProbability":10},{"ContentId":2,"SettingMethodList":[{"SettingMethod":2,"SettingValues":"9,8,7,6","Probability":10}],"AwardProbability":0},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10}],"AwardProbability":0}]}]}}
  
失敗範例：
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
  {"status":1112,"msg":"寶箱所有獎項機率加總超過100","data":{}}
```

## BoxTemplateCreate - 建立寶箱樣板
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxTemplateCreate.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  TemplateName(string)：樣板名稱
  BoxCoolDownTime(int)：冷卻時間
  BoxStartDateTime(string)：出現時間
  BoxEndDateTime(string)：消失時間
  BoxContents(object array)：參照 BoxContentSetting API
傳入範例：
  data={"OfficialId":1,"TemplateName":"樣版名稱1","BoxCoolDownTime":5,"BoxStartDateTime":"2023-02-16 00:00:00","BoxEndDateTime":"2023-02-28 00:00:00","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10 }],"AwardProbability":10},{"ContentId":2,"SettingMethodList":[{"SettingMethod":2,"SettingValues":"9,8,7,6","Probability":10 }],"AwardProbability":0},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10 }],"AwardProbability":0}]}
```

```
回傳方式：JSON
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
  {"status":1105,"msg":"寶箱內容缺失","data":{}}
  {"status":1112,"msg":"寶箱所有獎項機率加總超過100","data":{}}
```

## BoxTemplateUpdate - 修改寶箱樣板
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxTemplateUpdate.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  TemplateId(int)：寶箱樣板ID
  TemplateName(string)：樣板名稱
  BoxCoolDownTime(string)：冷卻時間
  BoxStartDateTime(string)：出現時間
  BoxEndDateTime(string)：消失時間
  BoxContents(object array)：參照 BoxContentSetting API
傳入範例：
  data={"OfficialId":1,"TemplateId":1,"TemplateName":"樣版名稱11","BoxCoolDownTime":10,"BoxStartDateTime":"2023-02-16 00:00:00","BoxEndDateTime":"2023-02-28 00:00:00","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10 }],"AwardProbability":20},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10 }],"AwardProbability":0}]}
```

```
回傳方式：JSON
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  參考共用錯誤代碼 或
  {"status":1105,"msg":"寶箱內容缺失","data":{}}
  {"status":1112,"msg":"寶箱所有獎項機率加總超過100","data":{}}
```

## BoxTemplateDelete - 刪除寶箱樣板
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxTemplateDelete.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  TemplateId(int)：寶箱樣板ID
傳入範例：
  data={"OfficialId":1,"TemplateId":1}
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

## BoxList - 寶箱列表
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
傳入範例：
  data={"OfficialId":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    BoxId(int)：寶箱ID
    BoxPosition(string)：寶箱定位
    BoxCoolDownTime(string)：冷卻時間 (分鐘)
    BoxStartDateTime(string)：出現時間
    BoxEndDateTime(string)：消失時間
    PlaceName(string)：地點名稱
    PlaceImg(string)：地點圖片
    PlaceDescribe(string)：地點描述
    BuildType(int)：建築類型,參照 https://docs.google.com/spreadsheets/d/1ACg-y_iwpOBTLO5kLnCzrWJte4eKC3h4HKJfv5Y_EHw/edit#gid=1873122037 普通建物的ID
    BoxContents(object array)：參照 BoxContentSetting API
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"BoxList":[{"BoxId":46,"BoxPosition":"999,10","BoxCoolDownTime":3,"BoxStartDateTime":"2023-01-17 00:00:00","BoxEndDateTime":"2023-01-21 00:00:00","PlaceName":"名稱測試","PlaceImg":"","PlaceDescribe":"描述測試","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":2,"MaxQuantity":11}],"AwardProbability":0},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10}],"AwardProbability":5}]}]}}
  
失敗範例：
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
```

## BoxCreate - 新增寶箱
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxCreate.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  OfficialId(int)：官方任務ID
  BoxPosition(string)：寶箱定位
  BoxCoolDownTime(string)：冷卻時間
  BoxStartDateTime(string)：出現時間
  BoxEndDateTime(string)：消失時間
  PlaceName(string)：地點名稱  
  PlaceDescribe(string)：地點描述
  BuildType(int)：建築類型,參照 https://docs.google.com/spreadsheets/d/1ACg-y_iwpOBTLO5kLnCzrWJte4eKC3h4HKJfv5Y_EHw/edit#gid=1873122037 普通建物的ID
  BoxContents(object array)：參照 BoxContentSetting API
傳入範例：
  data={"OfficialId":1,"BoxPosition":"123,456","BoxAddress":"test","BoxCoolDownTime":5,"BoxStartDateTime":"2023-02-16 00:00:00","BoxEndDateTime":"2023-02-28 00:00:00","PlaceName":"地點名稱測試","PlaceDescribe":"地點描述測試","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10}],"AwardProbability":0},{"ContentId":2,"SettingMethodList":[{"SettingMethod":2,"SettingValues":"9,8,7,6","Probability":10 }],"AwardProbability":0},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10}],"AwardProbability":0}]}
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"無此任務","data":{}}
  {"status":1105,"msg":"寶箱內容缺失","data":{}}
  {"status":1112,"msg":"寶箱所有獎項機率加總超過100","data":{}}
```

## BoxModify - 修改寶箱
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxModify.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  BoxId(int)：寶箱ID
  BoxPosition(string)：寶箱定位
  BoxCoolDownTime(string)：冷卻時間
  BoxStartDateTime(string)：出現時間
  BoxEndDateTime(string)：消失時間
  PlaceName(string)：地點名稱  
  PlaceDescribe(string)：地點描述
  BuildType(int)：建築類型,參照 https://docs.google.com/spreadsheets/d/1ACg-y_iwpOBTLO5kLnCzrWJte4eKC3h4HKJfv5Y_EHw/edit#gid=1873122037 普通建物的ID
  BoxContents(object array)：參照 BoxContentSetting API
傳入範例：
  data={"BoxId":46,"BoxPosition":"999,10","BoxAddress":"ttt","BoxCoolDownTime":3,"BoxStartDateTime":"2023-01-17 00:00:00","BoxEndDateTime":"2023-01-21 00:00:00","PlaceName":"名稱測試","PlaceDescribe":"描述測試","BoxContents":[{"ContentId":1,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":2,"MaxQuantity":11}],"AwardProbability":0},{"ContentId":3,"SettingMethodList":[{"SettingMethod":1,"MinQuantity":1,"MaxQuantity":10 }],"AwardProbability":5}]}
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
  參考共用錯誤代碼 或
  {"status":1105,"msg":"寶箱內容缺失","data":{}}
  {"status":1106,"msg":"查無此寶箱","data":{}}
  {"status":1112,"msg":"寶箱所有獎項機率加總超過100","data":{}}
```

## BoxModifyImage - 修改寶箱圖片
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
  BoxId(int)：寶箱ID
```

```
URL：api/inrocklife/backend/task/BoxModifyImage.php
Content-Type：multipart/form-data
傳入參數：
  PlaceImg：FILE 地點圖片 (一般圖檔上傳)
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
  參考共用錯誤代碼 或
  {"status":1106,"msg":"查無此寶箱","data":{}}
```

## BoxDelete - 刪除寶箱
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
URL：api/inrocklife/backend/task/BoxDelete.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  BoxId(int)：寶箱ID
傳入範例：
  data={"BoxId":1}
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
