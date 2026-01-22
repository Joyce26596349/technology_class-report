---
layout: default
---

<style>
    /* 1. 徹底移除側邊欄，釋放所有右側空間 */
    aside#sidebar, footer, .view { display: none !important; }
    
    /* 2. 強制內容區塊橫向擴展，並移除主題的浮動限制 */
    section#main_content { 
        width: 100% !important; 
        max-width: 1300px !important; /* 加寬到 1300px */
        margin: 0 auto !important; 
        float: none !important; 
        display: block !important;
        padding: 40px 20px !important;
    }

    /* 3. 按鈕容器：強制橫向排列且不允許擠壓 */
    .card-container {
        display: flex;
        gap: 30px;
        margin: 40px 0;
        width: 100%;
        justify-content: center;
        flex-wrap: nowrap; /* 禁止換行 */
    }

    /* 4. 卡片樣式：鎖定寬度比例 */
    .card {
        /* flex: 1 0 45% 代表：平分空間、不允許縮小、基礎寬度為 45% */
        flex: 1 0 45%; 
        box-sizing: border-box;
        padding: 50px 30px;
        border: 1px solid #e1e4e8;
        border-radius: 20px;
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        min-height: 400px;
        transition: all 0.3s ease;
        box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    }
    
    .card:hover {
        transform: translateY(-10px);
        box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        border-color: #007bff;
    }

    /* 標題與文字：防止變形 */
    .card-title { 
        font-size: 2.2em; 
        font-weight: bold; 
        color: #007bff; 
        margin-bottom: 20px;
        display: block;
        min-width: 200px; /* 防止標題被擠壓 */
    }
    
    .card-desc { 
        font-size: 1.2em; 
        color: #444; 
        margin-bottom: 30px; 
        line-height: 1.6;
        display: block;
    }

    /* 5. 藍色按鈕樣式 */
    .btn-ui {
        display: block;
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
