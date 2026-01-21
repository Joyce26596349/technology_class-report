---
layout: default
---

<style>
    /* 1. 徹底隱藏側邊欄、頁首、以及底部的所有維護與主題資訊 */
    header, aside, .sidebar, footer, .footer, #sidebar-content, .header-inner { 
        display: none !important; 
    }

    /* 2. 讓報告內容區域滿版並置中，移除所有左側空白 */
    .wrapper, section, .main-content {
        max-width: 1000px !important;
        margin: 0 auto !important;
        padding: 40px 20px !important;
        float: none !important;
        width: 100% !important;
    }
</style>



# 臺北市私立薇閣高級中學 114 學年度第 1 學期 工程專題
## 一、主題:
<details open>
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

## 三、建立模型挖掘資料：
<details>
  <summary>展開</summary>
<table style="width: 100%; table-layout: auto;">
  <tr align="center">
    <th width="10%">項目</th>
    <th width="30%">SqueezeNet</th>
    <th width="30%">alexnet</th>
    <th width="30%">參數</th>
  </tr>
  <tr>
    <td align="center"><b>增加訓練資料</b></td>
    <td colspan="2" align="center">
      <img src="https://github.com/user-attachments/assets/0a035af9-cbf4-4e80-b96a-2c16845d5376" height="200">
    </td>
    <td valign="top" style="white-space: nowrap;">
      <b>增加訓練資料內容</b><br>
      Observations: 資料量(28x3=84)<br>
      Classes: 類別數(3)<br>
      Most/Fewest observations: (28)<br>
      最高/最低資料數的類別(小批次大小)
    </td>
  </tr>

  <tr>
    <td align="center"><b>properties</b></td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/be4761ac-4dbc-4b96-8875-53365b7b8646" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/0a12b74c-1069-4c56-9fd2-e7eee3562de6" height="200">
    </td>
    <td valign="top" style="white-space: nowrap;">
      <b>更改參數</b><br>
      - NumFilters辦成有的類別數量3 <br>
      - WeightLearnRateFactor(權重學習率因子)調成10(更快) <br>
      - BiasLearnRateFactor(偏重學習率因子)調成10(和權重學習率因子一樣)
    </td>
  </tr>

  <tr>
    <td align="center"><b>analyze</b></td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/6548f0b0-4969-440d-acde-a21f5505b994" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/33a8d8d4-db51-488a-840f-0a9894652c80" height="200">
    </td>
    <td></td>
  </tr>

  <tr>
    <td align="center"><b>Training option</b></td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/c849fb2c-0a58-4e83-b6d4-a604ec665ff0" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/d1a4773e-c743-4cfd-8432-f1a5750febaa" height="200">
    </td>
    <td valign="top" style="white-space: nowrap;">
      <b>更改參數</b><br>
      ValidationFrequency: 類別數(3)<br>
      MaxEpochs: 最大訓練回合數(8)<br>
      MiniBatchSize: 小批次大小(28)
    </td>
  </tr>

  <tr>
    <td align="center"><b>訓練曲線</b></td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/1c1011a5-0dcd-4956-841f-f5530ebdbe97" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/30e0e185-c20a-427b-a525-92a47132ec4a" height="200">
    </td>
    <td></td>
  </tr>
</table>

</details>


## 四、實驗結果
<details>
  <summary>展開</summary>
  預測類別程式

  ```cpp
I = imread("XXX.jpg"); // 讀入圖片
I = imresize(I, [227 227]); // 調整圖片大小
[YPred,probs] = classify(trainedNetwork_1,I);
// 用訓練好的神經網絡分類，YPred : 預測的類別，probs : 每個類別的機率
imshow(I) // 顯示圖片
label = YPred; // 將預測的類別賦予給名為標籤的變數
title(string(label) + ", " + num2str(100*max(probs),3) + "%"); // 顯示類別與判斷率

```
實驗皆成功
<details>
<summary> 展開圖片成果 </summary>
                   
|SqueezeNet|AlexNet|
|:--:|:--:|
|<img src="https://github.com/user-attachments/assets/1f1f8dc8-8c1e-4904-94fd-7c295b4afd79" height="300"> | <img src="https://github.com/user-attachments/assets/d488bfea-b442-4cdf-a5e9-0a859162a3d4" height="300">|
|$\color{green}{\text{成功}}$ | $\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/ee41ae69-cb56-4133-bbe4-65a4386474b8" height="300"> | <img src="https://github.com/user-attachments/assets/31a977f7-0917-4a12-a6f5-f3aba7cf5eb9" height="300">|
|$\color{green}{\text{成功}}$ | $\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/d10462ec-a7fe-4b65-b48b-7011e3a65c6b" height="300"> | <img src="https://github.com/user-attachments/assets/06aed695-8f31-4f20-8ff0-4ee609ee88d4" height="300">|
|$\color{green}{\text{成功}}$ | $\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/e1ffd7d3-3899-46b6-a12c-d92c98cffc3f" height="300"> | <img src="https://github.com/user-attachments/assets/c5ca6055-f455-4ea7-b1e9-53f3fa8f721b" height="300">|
|$\color{green}{\text{成功}}$ | $\color{green}{\text{成功}}$|
</details>
</details>

## 五、實驗結果討論
<details>
  <summary>展開</summary>
  在這次的實驗中，SqueezeNet和Alexnet都訓練模型能夠成功辨識卷雲、積雲與層雲且信心度差不多，並以極高的信心度顯示出正確的答案，代表兩者在小型資料集下仍能展現良好的分類能力，但因為選取訓練資料時是用人工選取且資料僅有 40 張，數量偏少，我又不認識各種的雲，因此選取的都是較有該雲朵特徵的圖來做訓練與判斷，相似度較高，導致訓練成果信心度較高，若遇到更複雜或混合型的雲朵影像，模型可能會出現誤判的情形，本次實驗驗證CNN可以做影像的分類，可以透過圖片的特徵來判斷分類，並有很高的信心度。

</details>

## 六、心得感想
<details>
  <summary>展開</summary>
  本次的訓練使用matlab中內建app (Deep Network Designer)內的Squeezenet與alexnet卷積神經網路(CNN)，先下載圖片，並批次轉換成同類型的圖片與大小，接下來打開Deep Network Designer中的Squeezenet，在data中匯入要訓練的資料庫，我所選擇的有40張，若其中圖片有格式不正確的就無法計入其中，無法匯入，在data中的value數字為training option中要更改的MiniBatchSize（小批量大小），我的結果為28，在training option中要更改的還有ValidationFrequency，更改為類別數，MaxEporchs為完整重複的訓練次數，我調整成8，接下來更改designer中的conv/fc的參數，將NumFilters改成有的類別數量，將WeightLearnRateFactor(權重學習率因子)調成10讓他更快，將BiasLearnRateFactor(偏重學習率因子)調成10，與權重學習率因子相同，接下來就可以訓練了。
在尋找圖片時使用google圖片搜尋雲朵類型，我發現google查詢內容常常是依照各網站有這個單詞的圖片來顯示，所以我在查詢這三種圖片時常找到同一張圖片，因此必須人工選取符合分類的照片，在使用圖片助手批量圖片下載器時，我選好了圖片並點選下載選中，他卻幫我下載所有的圖片，經過多次摸索以後，必須要先按保留選中，將不要的刪掉，下載才會是我需要的圖片。
天空中的雲朵曾不能以一瞬，雲朵形狀依天氣氣流、形成高度、氣溫、濕度、等條件的不同而變成不同的形狀，因此選取主題時是想讓AI幫我判斷雲朵類型，因為我看不出天空中各個雲朵是什麼雲，在篩選google圖片時只能利用大致雲朵類型的形狀來決定要不要選擇類似圖片，所以圖庫中的雲朵可能較相似，讓AI比較好判斷類型以及給出較高的信心度，造成我給他判斷的圖片都是回答成功的且判斷率也相當的高。


</details>
