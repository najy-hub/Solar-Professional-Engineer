<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>كورس الطاقة الشمسية - 14 أسبوع</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #f2f2f2;
      padding: 20px;
      color: #333;
    }

    h1 {
      text-align: center;
      color: #005b4f;
      margin-bottom: 10px;
    }

    p.intro {
      text-align: center;
      margin-bottom: 30px;
    }

    .week {
      margin-bottom: 30px;
      padding: 15px;
      background: #ffffff;
      border-radius: 14px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
      border: 1px solid #ddd;
    }

    .week.locked {
      opacity: 0.4;
      pointer-events: none;
    }

    .week h2 {
      font-size: 20px;
      margin-bottom: 15px;
      color: #007b7f;
    }

    .lecture {
      margin: 20px auto;
      padding: 15px;
      background: #fff;
      border: 1px solid #ccc;
      border-radius: 16px;
      max-width: 850px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    iframe {
      width: 100%;
      height: 1080px;
      border-radius: 12px;
      display: block;
      margin: 0 auto;
    }

    .locked .lecture span {
      display: block;
      font-style: italic;
      color: #999;
      text-align: center;
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <h1>كورس الطاقة الشمسية</h1>
  <p class="intro">يتكون هذا الكورس من 14 أسبوعًا، كل أسبوع يحتوي على 5 محاضرات. يتم فتح المحتوى تدريجيًا أسبوعيًا.</p>

  <div id="course-content"></div>

  <script>
    const startDate = new Date("2025-07-01"); // ✅ تاريخ بداية الكورس
    const totalWeeks = 14;
    const lecturesPerWeek = 5;
    const today = new Date();
    const courseContent = document.getElementById("course-content");

    // ✅ روابط Bunny للفيديوهات
    const bunnyVideos = {
      1: "https://iframe.mediadelivery.net/play/460802/dce4ee28-5099-44df-9760-dddcf3609a95",
      2: "https://
