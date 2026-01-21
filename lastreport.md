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
 <table>
  <tr align="center">
    <th width="35%">SqueezeNet</th>
    <th width="35%">alexnet</th>
    <th width="30%">更改參數</th>
  </tr>
  
  <tr>
    <td align="center">
      <div align="center"><b>Training option</b></div>
      <img src="https://github.com/user-attachments/assets/c849fb2c-0a58-4e83-b6d4-a604ec665ff0" height="200">
    </td>
    <td align="center">
      <div align="center"><b>Training option</b></div>
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
    <td colspan="3" align="center">
      <b>Squeezenet訓練曲線</b><br>
      <img src="Squeezenet_Curve_連結" height="200">
    </td>
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
|:--|:--|
|<img src="https://github.com/user-attachments/assets/af0bf8f7-ba7e-4975-945b-5b2a35eb83aa" height="300"> | <img src="https://github.com/user-attachments/assets/ab4b77a8-bfc1-4489-8882-9ea4ba1a8bdc" height="300">|
|$\color{green}{\text{成功}}$|$\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/5f111314-6d78-4c23-b80f-9434726e152b" height="300">|<img src="https://github.com/user-attachments/assets/da13ed0b-a031-4201-9990-ff07564096ab" height="300">|
|$\color{green}{\text{成功}}$|$\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/130048f4-3c7c-4f6e-9694-3c7bb70d8967" height="300">|<img src="https://github.com/user-attachments/assets/f82da63f-8f38-41ce-99d1-f00bff1f3e44" height="300">|
|$\color{green}{\text{成功}}$|$\color{green}{\text{成功}}$|
|<img src="https://github.com/user-attachments/assets/f117bb4c-201a-436a-bd5f-202de333dfa5" height="300"> | <img src="https://github.com/user-attachments/assets/24b6c266-f846-41a6-8f69-1088eb73ce36" height="300">|
|$\color{green}{\text{成功}}$|$\color{green}{\text{成功}}$|
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
