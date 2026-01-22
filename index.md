---
layout: default
---

<style>
    /* 1. 隱藏側邊欄與頁尾 */
    aside#sidebar, footer, .view { display: none !important; }
    
    /* 2. 頁面加寬至 1200px */
    section#main_content { 
        width: 100% !important; 
        max-width: 1200px !important; 
        margin: 0 auto !important; 
        float: none !important; 
    }

    /* 3. 按鈕容器：強制平分寬度 */
    .card-container {
        display: flex;
        gap: 30px;            /* 兩個框框之間的間距 */
        margin: 40px 0;
        align-items: stretch; /* 高度對齊 */
        width: 100%;
    }

    /* 4. 卡片樣式：確保寬度 1:1 */
    .card {
        flex: 1 1 0;          /* 這是關鍵：強制兩個框框平分剩餘空間，寬度絕對一致 */
        width: 0;             /* 防止內容撐開導致寬度不一 */
        padding: 50px 40px;
        border: 1px solid #e1e4e8;
        border-radius: 20px;
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        min-height: 380px;
        transition: all 0.3s ease;
        box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    }
    
    .card:hover {
        transform: translateY(-10px);
        box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        border-color: #007bff;
    }

    /* 文字樣式優化 */
    .card-title { 
        font-size: 2em; 
        font-weight: bold; 
        color: #007bff; 
        margin-bottom: 20px;
        display: block;
        white-space: nowrap; /* 避免標題換行擠壓空間 */
    }
    
    .card-desc { 
        font-size: 1.15em; 
        color: #444; 
        margin-bottom: 40px; 
        line-height: 1.6;
        word-wrap: break-word; /* 確保長文字會自動折行而不撐開框框 */
    }

    /* 5. 按鈕樣式 */
    .btn-ui {
        display: inline-block;
        padding: 15px 0;
        width: 100%;           
        background-color: #007bff;
        color: white !important;
        border-radius: 10px;
        font-weight: bold;
        font-size: 1.2em;
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
