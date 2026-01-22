---
layout: default
---

<style>
    /* 1. 隱藏右側欄位與頁尾，釋放空間 */
    aside#sidebar, footer, .view { display: none !important; }
    
    /* 2. 讓主內容區域變寬 (從 900px 提升到 1100px) */
    section#main_content { 
        width: 100% !important; 
        max-width: 1100px !important; 
        margin: 0 auto !important; 
        float: none !important; 
    }

    /* 3. 按鈕容器：橫向並排 */
    .card-container {
        display: flex;
        gap: 30px;            /* 增加兩個框框之間的間距 */
        margin: 40px 0;
        justify-content: center;
    }

    /* 4. 框框（卡片）樣式：加大並增加高度 */
    .card {
        flex: 1;
        max-width: 500px;      /* 限制單個框框最大寬度 */
        padding: 40px 30px;    /* 增加內部留白，讓框框看起來更大 */
        border: 1px solid #e1e4e8;
        border-radius: 15px;   /* 圓角加大 */
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between; /* 確保內容在頂部，按鈕在底部 */
        min-height: 320px;     /* 強制框框高度一致 */
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 8px 20px rgba(0,0,0,0.06);
    }
    
    .card:hover {
        transform: translateY(-8px);
        box-shadow: 0 15px 30px rgba(0,0,0,0.12);
        border-color: #007bff;
    }

    /* 標題樣式 */
    .card-title { 
        font-size: 1.8em; 
        font-weight: bold; 
        color: #007bff; 
        margin-bottom: 20px;
        display: block;
    }
    
    /* 描述文字樣式 */
    .card-desc { 
        font-size: 1.1em; 
        color: #586069; 
        margin-bottom: 30px; 
        line-height: 1.6;
    }

    /* 5. 真實按鈕樣式 */
    .btn-ui {
        display: inline-block;
        padding: 12px 0;
        width: 100%;           /* 按鈕寬度撐滿 */
        background-color: #007bff;
        color: white !important;
        border-radius: 8px;
        font-weight: bold;
        font-size: 1.1em;
        text-decoration: none !important;
        transition: background-color 0.2s;
    }
    .btn-ui:hover {
        background-color: #0056b3;
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
