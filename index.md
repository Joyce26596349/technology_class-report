---
layout: default
---

<style>
    /* 1. 隱藏右側欄位與 Architect 主題原本的頁尾資訊 */
    aside#sidebar, footer, .view { display: none !important; }
    
    /* 2. 極致加寬：將原本的寬度限制打開到 1200px */
    section#main_content { 
        width: 95% !important; 
        max-width: 1200px !important; 
        margin: 0 auto !important; 
        float: none !important; 
        padding-top: 50px;
    }

    /* 3. 按鈕容器：橫向並排佈局 */
    .card-container {
        display: flex;
        gap: 40px;            /* 增加兩個大框框之間的距離 */
        margin: 20px 0;
        justify-content: center;
        align-items: stretch; /* 確保兩個框框高度永遠保持一致 */
    }

    /* 4. 加大版框框（卡片）樣式 */
    .card {
        flex: 1;
        padding: 50px 40px;    /* 增加內部空間，讓標題與內容不擁擠 */
        border: 1px solid #e1e4e8;
        border-radius: 20px;   /* 更圓潤的轉角 */
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        min-height: 380px;     /* 增加框框的基本高度 */
        transition: all 0.3s ease;
        box-shadow: 0 10px 30px rgba(0,0,0,0.08); /* 更柔和的陰影 */
    }
    
    .card:hover {
        transform: translateY(-10px); /* 懸停時浮起更高 */
        box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        border-color: #007bff;
    }

    /* 標題字體加大 */
    .card-title { 
        font-size: 2em; 
        font-weight: bold; 
        color: #007bff; 
        margin-bottom: 25px;
        display: block;
    }
    
    /* 描述文字加大 */
    .card-desc { 
        font-size: 1.2em; 
        color: #444; 
        margin-bottom: 40px; 
        line-height: 1.7;
    }

    /* 5. 強化版藍色按鈕 */
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
        transition: background 0.2s;
    }
    .btn-ui:hover {
        background-color: #0056b3;
        box-shadow: 0 4px 12px rgba(0,123,255,0.3);
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
