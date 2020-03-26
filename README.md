# 線上教學串流平台

基于 Spring Boot 和 [SRS](https://github.com/ossrs/srs)

## 平台功能

* 影片串流
* 在线聊天
* 串流提醒
* 作業上傳和批改

## live-teaching-platform 使用教學（on Mac）
1. 使用docker安裝mysql、srs:
```
docker run --name mysql  -p 3306:3306 -e MYSQL_ROOT_PASSWORD=ibdo -d mysql:5.6
```
```
docker run -p 1935:1935 -p 1985:1985 -p 8082:8080 ossrs/srs:3
```
2. mysql內建一個upload_video的DB
3. 下載SpringToolSuite, https://spring.io/tools
4. 安裝JDK
5. 導入live-teaching-platform專案 -> 選擇Maven Project 
6. 打開`src/main/resources/application.properties`
修改數據庫ip、直播服務器ip、存放路徑...等
7. 點擊Run As -> Spring Boot App
8. 打開localhost:8080查看
9. 下拉選單空白的處理方法：
資料庫裡面course及major的表內新增資料即可
- - - -
## 使用OBS 開始直播並推送到SRS伺服器
1. 根據上部docker安裝的SRS，本地推送伺服器ip為：
> rtmp:  
> rtmp://127.0.0.1/live/**livestream** <- 可自訂  
> http:  
> http://127.0.0.1/live/**livestream** <- 可自訂  
2. OBS設定：
服務：自定義
伺服器： http://127.0.0.1/live/**livestream** <- 可自訂
串流金鑰：在網站上開啟直播即可查看
![](https://github.com/r041291867/live-teaching-platform/raw/master/images/srs01.png)
3. 設定完成後點擊“開始捕獲”，看是否出現錯誤訊息
4. 若無，則進入localhost:1985、點擊預覽查看是否成功串流
![](https://github.com/r041291867/live-teaching-platform/raw/master/images/srs02.png)

