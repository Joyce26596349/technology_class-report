---
layout: default
---

<style>
    /* 隱藏 Architect 主題的側邊欄、維護者資訊與頁尾 */
    header aside, .inner footer, .sidebar, footer, .view { display: none !important; }
    
    /* 調整版面為滿版置中 */
    #main_content { width: 100% !important; max-width: 900px !important; margin: 0 auto !important; }
    header { padding: 30px 0 !important; }

    /* 卡片式按鈕設計 */
    .card-container { display: flex; gap: 20px; margin-top: 30px; flex-wrap: wrap; }
    .card {
        flex: 1; min-width: 280px; padding: 25px; border: 1px solid #e0e0e0;
        border-radius: 12px; background-color: #ffffff; text-align: center;
        text-decoration: none !important; color: #333 !important; display: block;
        transition: transform 0.2s, box-shadow 0.2s;
    }
    .card:hover { transform: translateY(-5px); box-shadow: 0 10px 20px rgba(0,0,0,0.1); }
    .card-title { display: block; font-size: 1.5em; font-weight: bold; color: #007bff; margin-bottom: 8px; }
    .card-desc { display: block; font-size: 1em; color: #666; margin-bottom: 20px; }
    .btn-start {
        display: inline-block; padding: 10px 30px; background-color: #007bff;
        color: white !important; border-radius: 6px; font-weight: bold;
    }
</style>

# 📚 工程專題學習總整理

這是一個有關工程研究報告的總整理

<div class="card-container">

<a href="mid_report" class="card">
    <span class="card-title">📊 期中報告</span>
    <span class="card-desc">結合了matlab和生程式AI的運用，並適用在實體創意主題上</span>
    <span class="btn-start">開始學習</span>
</a>

<a href="last_report" class="card">
    <span class="card-title">☁️ 期末報告</span>
    <span class="card-desc">使用 matlab 中 deep network designer 判斷出圖片中天空中不同雲朵的類型 </span>
    <span class="btn-start">開始學習</span>
</a>

</div>
