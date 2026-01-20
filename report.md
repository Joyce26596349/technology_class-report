# 工程專題期中報告 MATLAB程式設計
## 前言
<details open>
<summary>展開</summary>
本三次實驗結合了matlab和生程式AI的運用，並適用在實體應用上，此實驗不僅能將程式運用在現實生活當中，還能比較不同AI對於程式的理解和表現的差異
這次的課程中有ch07握把式圖形與GUI設計、ch08二維圖形、ch09三維圖形、ch11多項式
、ch16影像與動畫
</details>

## 主題一：拋體運動繪圖
<details>
<summary>展開</summary>

  ### 大綱
為了解決物理老師畫拋物線太不準確而被同學罵的問題，本實驗利用ch08二維圖形依照使用者的輸入繪製出一個拋物線，並標示順便計算一些基本的相關數據，例如:最大高度、時間、射程...
  ### 實作

<details>
  <summary>展開圖片</summary>
  <img src="https://github.com/user-attachments/assets/9dd7a445-63e7-416d-8682-7555f7254633" width="500">
</details>
<details>
  <summary>重要程式整理</summary>
  
```cpp
clear; clc; close all;
% 使用者輸入
h0 = input('請輸入初始高度 (m): ');
v0 = input('請輸入初始速率 (m/s): ');
theta_deg = input('請輸入發射角度 (度): ');
theta = deg2rad(theta_deg);% 單位轉換
g = 9.81;% 重力加速度 (m/s²)
v0x = v0 * cos(theta);% x初始速度分量
v0y = v0 * sin(theta);% y初始速度分量
% 二次方程求解：-0.5*g*t² + v0y*t + h0 = 0
a = -0.5 * g;
b = v0y;
c = h0;
t_flight = (-b - sqrt(b^2 - 4*a*c)) / (2*a);% 落地時間
R = v0x * t_flight;% 射程R
% 計算最大高度H
if v0y > 0
   t_max_height = v0y / g;
   H = h0 + v0y * t_max_height - 0.5 * g * t_max_height^2;
else
   H = h0;  % 若初始垂直速度向下，最大高度就是初始高度
end
% 生成軌跡數據
t = linspace(0, t_flight, 1000);
x = v0x * t;
y = h0 + v0y * t - 0.5 * g * t.^2;
% 繪製軌跡
plot(0, h0, 'ro', 'MarkerSize', 8, 'MarkerFaceColor', 'red', 'DisplayName', '起點');
hold on;
plot(R, 0, 'go', 'MarkerSize', 8, 'MarkerFaceColor', 'green', 'DisplayName', '落點');
grid on;
xlabel('水平距離 (m)', 'FontSize', 12);
ylabel('高度 (m)', 'FontSize', 12);
title('拋體運動軌跡', 'FontSize', 14);
% 加入重要標註
text(0.1, h0+0.1, sprintf('起點 (0, %.1f)', h0), 'FontSize', 9, 'Color', 'red');
text(R*0.95, max(y)*0.1, sprintf('落點 (%.1f, 0)', R), 'FontSize', 9, 'Color', 'green');
text(x_max*1.02, ymax*0.95, sprintf('最高點\n(%.1f, %.1f)', x_max, ymax), 'FontSize', 9, 'Color', 'magenta');
% 設定座標軸範圍
axis equal;
xlim([0, max(x)*1.15]);
ylim([0, max(y)*1.15]);
text(x_range*0.02, y_range*0.95, '拋體運動分析', 'FontSize', 11, 'FontWeight', 'bold', 'Color', 'blue');% 標題
```
</details>

### 心得
本次實驗與chatdeepseek合作，因為平時使用這個生成式AI來解物理的正確率非常的高，因此我選擇它來進行這次的實驗，而結果也十分順利，很快就溝通好了相關的內容，還多出了一些出乎我意料的資訊，並繪製出一個拋物線，使用者先輸入他的初始高度、初始速度、初始角度，程式運行就會繪製出他的拋物線並顯示出他的相關數據加上圖例，利用ch08二維圖形所教的plot, text, axis, hold on…等函式輸入初速度、角度與高度後，程式能自動繪出完整的拋物線軌跡，並計算最大高度、飛行時間與射程等相關數據，我常常在習題繪製拋物線時畫的不精確，導致數據算出來和圖對不上而開始懷疑自我，而運用科技的力量可以很好的幫助減緩這件事的發生，這個程式大致利用二次方程求飛行時間 t ，用間隔linspace畫出連續軌跡，再利用text標註數據在圖上 ，最後利用plot將拋物線的各項數據呈現在圖片上就完成了

</details>

# 主題二：猜圖片
<details>
<summary>展開</summary>

  ### 大綱
本實驗利用ch16影像與動畫製作出一個小遊戲，這個小遊戲是會在matlab內建圖片中隨機選擇一張照片，照片會從解析度最低的部分顯示，猜錯了就會慢慢提高解析度
  ### 實作

<details>
  <summary>展開圖片</summary>

  <img src="https://github.com/user-attachments/assets/0e7c380b-212a-4c2c-b814-4652c9b48d1a" width="500">
  </details>
<details>
  <summary>重要程式整理</summary>
  
```cpp
function guessTheImageBuiltIn()
   % MATLAB 內建的圖片檔案名稱列表 (Image Processing Toolbox 內建的示範圖片)
   imageNames = {...};
   % 圖片內容的對應答案
   possibleAnswers = {...};
   % 隨機選擇一張圖片的索引
   randIndex = randi(length(imageNames));
   selectedImageName = imageNames{randIndex};
   correctAnswer = possibleAnswers{randIndex};
   try
       % 讀取內建圖片
       originalImage = imread(selectedImageName);
       if ~isa(originalImage, 'uint8') && ~isa(originalImage, 'uint16')
            [imgData, map] = imread(selectedImageName);
            if ~isempty(map)
                originalImage = ind2rgb(imgData, map);
            end
       end
       if size(originalImage, 3) == 4
           originalImage = originalImage(:,:,1:3);
       end
   catch ME
       disp(['錯誤：無法讀取內建圖片檔案：' selectedImageName]);
       disp('錯誤訊息：');
       disp(ME.message);
       disp('可能您的 MATLAB 版本沒有 Image Processing Toolbox 或該檔案不存在。');
       return;
   end
   downsampleFactors = [32, 16, 8, 4, 2, 1];% 從低的解析度開始
   % 創建並獲取 Figure 句柄，以確保圖形視窗穩定
   hFig = figure('Name', '猜猜看遊戲：解析度漸進提高', 'NumberTitle', 'off');
   isGuessed = false;
   for k = 1:length(downsampleFactors)
       if isGuessed
           break;
       end
       factor = downsampleFactors(k);
       % 影像處理：模擬極低解析度/像素化效果
       if factor > 1
           % 1. 降採樣 (Downsample)
           lowResImage = imresize(originalImage, 1/factor, 'Method', 'nearest');
           % 2. 升採樣回原始大小 (Upsample) 以保持視窗大小不變
           currentImage = imresize(lowResImage, size(originalImage, [1 2]), 'Method', 'nearest');
       else
           currentImage = originalImage;% factor = 1 時，顯示原始圖片
       end
       % 顯示當前圖片
       figure(hFig);
       imshow(currentImage);
       title(sprintf('猜猜看 - 階段 %d/%d (解析度因子 1/%d)', k, length(downsampleFactors), factor));
       drawnow;
       pause(0.05);
       fprintf('--- 階段 %d (解析度因子 1/%d) ---\n', k, factor);
       userGuess = input('您的猜測是 (輸入文字，或輸入 "pass" 跳過)：', 's');% 讓使用者輸入猜測
       if strcmpi(strtrim(userGuess), 'pass')% 檢查輸入
           fprintf('您選擇等待下一階段...\n\n');
           pause(1);
           continue;
       elseif strcmpi(strtrim(userGuess), correctAnswer)
           % 猜對了！
           fprintf('\n🎉 **恭喜您！猜對了！** 正確答案是：「%s」。\n', correctAnswer);
           isGuessed = true;
       else
           % 猜錯了
           fprintf('\n😞 猜錯了。您猜的是：「%s」。請再試一次或等待下一階段。\n\n', strtrim(userGuess));
       end
   end
   % 遊戲結束
   if ~isGuessed
       fprintf('\n--- 遊戲結束 ---\n');
       fprintf('很抱歉，您沒有在最高解析度階段猜對。\n');
   end
   % 顯示最終原始圖片
   figure(hFig);
   imshow(originalImage);
   title(sprintf('遊戲結束 - 正確答案：「%s」', correctAnswer));
end


```
</details>

### 心得
本次實驗與gemini合作，因為他可生成圖片，所以我認為他的圖片處理應該較好、在三種AI中，我發覺他是AI中回答最快，而且他會加表情符號，感覺比較親切，這個遊戲是隨機生成圖片，並將解析度調低，會先將有的選項顯示出來，讓人較方便選擇答案，輸入後，程式會判斷使用者的輸入是否正確，若為錯誤，將會將解析度調高一個階段，並讓人繼續猜，總共有五個階段，猜對後會顯示猜對的字樣，並將解析度調回原本的狀態，公布答案，這個小遊戲好玩，讓人有種欲罷不能的感覺，若是可以增加更多的圖片就可以讓猜題更有挑戰性。

</details>

# 主題三：表單製造器 
<details>
<summary>展開</summary>
  
  ### 大綱
本實驗利用ch07握把式圖形與GUI設計撰寫了一個表單製造器，可增加多個題目並選擇不同答題方式，也可以將任意一個問題刪除，右側預覽區可以顯示當前表單狀態
  ### 實作

<details>
  <summary>展開圖片</summary>

  <img src="https://github.com/user-attachments/assets/51706af9-524c-4d1a-96a1-70301e28b576" width="500">
  </details>
<details>
  <summary>重要程式整理</summary>
  
```cpp
function formbuilder
clear; clc; close all;
questions = struct('type', {}, 'text', {}, 'options', {});
%% 視窗與面板佈局
fig = figure('Name','表單製造器 v4 - 從上到下排列','Position',[200 100 950 600], ...
   'MenuBar','none','ToolBar','none','NumberTitle','off','Color',[0.98 0.98 0.98]);
ctrlW = 0.3;
previewW = 1-ctrlW;
ctrlPanel = uipanel(fig,'Title','控制面板','FontWeight','bold','FontSize',11, ...
   'Position',[0 0 ctrlW 1]);
previewPanel = uipanel(fig,'Title','表單預覽','FontWeight','bold','FontSize',11, ...
   'Position',[ctrlW 0 previewW 1],'BackgroundColor','white');
% 控制區
listboxQ = uicontrol(ctrlPanel,'Style','listbox','Units','normalized', ...
   'Position',[0.05 0.45 0.9 0.5],'String',{});
popupType = uicontrol(ctrlPanel,'Style','popupmenu','Units','normalized', ...
   'Position',[0.05 0.34 0.9 0.06], ...
   'String',{'短答案','段落','單選','複選','下拉式選單'});
uicontrol(ctrlPanel,'Style','pushbutton','String','新增題目', ...
   'Units','normalized','Position',[0.05 0.26 0.42 0.06],'Callback',@cbAdd);
uicontrol(ctrlPanel,'Style','pushbutton','String','刪除題目', ...
   'Units','normalized','Position',[0.53 0.26 0.42 0.06],'Callback',@cbDelete);
uicontrol(ctrlPanel,'Style','pushbutton','String','清除全部', ...
   'Units','normalized','Position',[0.05 0.17 0.9 0.06],'Callback',@cbClear);
% 初始狀態
updateList();
rebuildPreview();
%callback
function cbAdd(~,~)
   types = get(popupType,'String');
   qtype = types{get(popupType,'Value')};
   qtext = inputdlg('輸入題目文字','新增題目',[1 60]);
   if isempty(qtext), return; end
   q.text = qtext{1};
   q.options = {};
   switch qtype
       case '短答案'
           q.type = 'short';
       case '段落'
           q.type = 'paragraph';
       case '單選'
           q.type = 'single';
           opt = inputdlg('輸入選項（以 | 分隔）','選項',[1 80]);
           if isempty(opt), return; end
           q.options = strtrim(strsplit(opt{1},'|'));
       case '複選'
           q.type = 'checkbox';
           opt = inputdlg('輸入選項（以 | 分隔）','選項',[1 80]);
           if isempty(opt), return; end
           q.options = strtrim(strsplit(opt{1},'|'));
       case '下拉式選單'
           q.type = 'dropdown';
           opt = inputdlg('輸入選項（以 | 分隔）','選項',[1 80]);
           if isempty(opt), return; end
           q.options = strtrim(strsplit(opt{1},'|'));
   end
   questions(end+1) = q;
   updateList();
   rebuildPreview();
end
function cbDelete(~,~)
   if isempty(questions), return; end
   sel = get(listboxQ,'Value');
   questions(sel) = [];
   updateList();
   rebuildPreview();
end
function cbClear(~,~)
   questions = struct('type', {}, 'text', {}, 'options', {});
   updateList();
   rebuildPreview();
end
function updateList()
   if isempty(questions)
       set(listboxQ,'String',{'(尚無題目)'},'Value',1);
   else
       strs = cell(1,numel(questions));
       for k=1:numel(questions)
           strs{k} = sprintf('%d. [%s] %s',k,questions(k).type,questions(k).text);
       end
       set(listboxQ,'String',strs,'Value',1);
   end
end

```
</details>

### 心得
本次實驗與chatGPT合作，我發覺與它聊天、更改程式內容時時常不符合我的預期或沒改進，不是一個東西改好了而原本正確的東西改成錯的，就是直接產生錯誤無法執行，與它溝通了非常多的時間才造就了最終的結果。
這個表單可以選擇答案形式(短答案,段落,單選,複選,下拉式選單)並新增問題，使用選擇的答案時將選項之間插入" | "即可分項，左上角選取題目可刪除該題目，下方有一鍵清除功能，雖然這個表單看起來很棒但還有值得改進的地方，例如可修改已寫完的題目內容、改變題目答題方式、增加可插入式題目、下載表單、每次更改題目時不將選項重置...。
</details>
