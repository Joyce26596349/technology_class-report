---
layout: default
---

<style>
    /* 1. 隱藏側邊欄、頁首標題、以及底部的維護資訊 (maintained by...) */
    header, aside, .sidebar, footer, .footer { 
        display: none !important; 
    }

    /* 2. 讓內容區域滿版並置中 */
    .wrapper, section {
        max-width: 900px !important;
        margin: 0 auto !important;
        padding: 40px 20px !important;
        float: none !important;
        width: 100% !important;
    }

    /* 3. 卡片容器設計 */
    .card-container {
        display: flex;
        gap: 20px;
        margin-top: 20px;
        flex-wrap: wrap;
    }
    .card {
        flex: 1;
        min-width: 280px;
        padding: 30px;
        border: 1px solid #e0e0e0;
        border-radius: 12px;
        background-color: #ffffff;
        text-align: center;
        text-decoration: none !important;
        transition: transform 0.2s;
        color: #333 !important;
        display: block;
    }
    .card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        background-color: #f8fbff;
    }
    .card-title { display: block; font-size: 1.6em; font-weight: bold; color: #007bff; margin-bottom: 10px; }
    .card-desc { display: block; font-size: 1.1em; color: #666; margin-bottom: 25px; }
    .btn-ui {
        display: inline-block;
        padding: 10px 40px;
        background-color: #007bff;
        color: white !important;
        border-radius: 6px;
        font-weight: bold;
    }
</style>

# 📚 工程專題學習總整理

這是一個有關工程研究報告的總整理

<div class="card-container">

<a href="mid_report" class="card">
<span class="card-title">📊 期中報告</span>
<span class="card-desc">matlab創意主題</span>
<span class="btn-ui">開始學習</span>
</a>

<a href="last_report" class="card">
<span class="card-title">☁️ 期末報告</span>
<span class="card-desc">不同卷積神經訓練AI</span>
<span class="btn-ui">開始學習</span>
</a>

</div>

---
