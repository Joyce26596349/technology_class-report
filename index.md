---
layout: default
---

<style>
    /* 1. 隱藏 Architect 主題原本的右側側邊欄與頁尾 */
    aside#sidebar, footer, .view { display: none !important; }
    
    /* 2. 讓內容區域滿版顯示，解決右邊空洞 */
    section#main_content { 
        width: 100% !important; 
        max-width: 1000px !important; 
        margin: 0 auto !important; 
        float: none !important; 
    }

    /* 3. 按鈕容器：改為 Flex 佈局實現並排 */
    .card-container {
        display: flex;
        gap: 20px;
        margin: 30px 0;
        flex-wrap: wrap; /* 手機版會自動換行 */
        justify-content: space-between;
    }

    /* 4. 重新定義卡片樣式，解決截圖中白塊縮小的問題 */
    .card {
        flex: 1; 
        min-width: 320px; /* 確保並排時有足夠寬度 */
        padding: 30px 20px;
        border: 1px solid #e1e4e8;
        border-radius: 12px;
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        display: flex;
        flex-direction: column;
        align-items: center;
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    }
    
    .card:hover {
        transform: translateY(-5px);
        box-shadow: 0 12px 25px rgba(0,0,0,0.1);
    }

    .card-title { 
        font-size: 1.5em; 
        font-weight: bold; 
        color: #007bff; 
        margin-bottom: 15px;
        display: flex;
        align-items: center;
        gap: 8px;
    }
    
    .card-desc { 
        font-size: 0.95em; 
        color: #586069; 
        margin-bottom: 25px; 
        line-height: 1.5;
        min-height: 3em; /* 讓兩個卡片描述高度一致 */
    }

    .btn-ui {
        padding: 10px 35px;
        background-color: #007bff;
        color: white !important;
        border-radius: 6px;
        font-weight: bold;
        text-decoration: none !important;
    }
</style>

# 📚 工程專題學習總整理

<div class="card-container">

<a href="mid_report" class="card">
    <span class="card-title">📊 期中報告</span>
    <span class="card-desc">結合了matlab和生程式AI的運用，並適用在實體創意主題上</span>
    <span class="btn-start">開啟報告</span>
</a>

<a href="last_report" class="card">
    <span class="card-title">☁️ 期末報告</span>
    <span class="card-desc">使用 matlab 中 deep network designer 判斷出圖片中天空中不同雲朵的類型 </span>
    <span class="btn-start">開啟報告</span>
</a>

</div>
