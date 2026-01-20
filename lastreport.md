# 臺北市私立薇閣高級中學 114 學年度第 1 學期 工程專題
## 一、主題:
<details>
<summary>展開</summary>
目標為使用 matlab 中 deep network designer 的 sqeezenet 與 alexnet 並判斷出天空中不同雲朵的類型,我蒐集了許多常見的雲朵照,包含卷雲(cirrus)、積雲(cumulus)、層雲(stratus),並進階轉換成相同格式與檔名,再調整訓練參數,訓練完後給他辨識和給的資料不一樣的圖,讓他分類與測試信心度,本次實驗希望可以將 AI 科技與地球科學結合,並讓天氣系統更好的利用雲朵自動預判天氣狀況。

| SqueezeNet | AlexNet |
| :--- | :--- |
| <img src="https://github.com/user-attachments/assets/df7fce61-e1a1-47a7-afde-b1d265c6f861" width="100"> |<img src="https://github.com/user-attachments/assets/97d1bb6b-ee3b-4896-963c-9aba2e56b1b7" width="103">|

</details>

## 二、收集資料：
<details>
<summary>展開</summary>
資料預處理+格式轉換 <img src="https://github.com/user-attachments/assets/0b95287e-81e0-4f3f-8119-3beed4750a6d" width="100"> 選擇批次轉換
  
| 將詢問改為取代並選擇資料夾 | 加入轉換為全彩、調整大小將寬度與高度調成227 | 全選並選擇批次重新命名並更改命名範本、勾選副檔名 |
| :--- | :--- | :--- |
| <img src="https://github.com/user-attachments/assets/1daa2d1d-9fc5-45a8-bca7-3f30c733a067" width="259"> | <img src="https://github.com/user-attachments/assets/3903abe3-7886-42e8-a3b5-47ebda8b6a4b" width="235"> | <img src="https://github.com/user-attachments/assets/268fb8ef-41e0-448b-8e33-e9f24ca21417" width="298"> |
</details>
