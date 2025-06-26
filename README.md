<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>رحلة المهندس المحترف - المحاضرات</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background: linear-gradient(to right, #0f0f0f, #1c1c1c);
      color: #fff;
      line-height: 1.6;
    }

    header {
      background-color: #111;
      padding: 20px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #333;
    }

    header h1 {
      font-size: 24px;
      color: #f9f9f9;
    }

    nav {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }

    nav button {
      background-color: #333;
      color: #fff;
      border: none;
      padding: 10px 16px;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    nav button:hover {
      background-color: #555;
    }

    nav button.locked {
      background-color: #222;
      cursor: not-allowed;
    }

    .content {
      padding: 40px 20px;
      max-width: 800px;
      margin: auto;
    }

    .locked-message {
      text-align: center;
      font-size: 18px;
      color: #ffba00;
      margin-top: 20px;
    }

    iframe {
      width: 100%;
      height: 400px;
      border-radius: 12px;
      border: none;
      margin-bottom: 20px;
    }

    h2 {
      margin-bottom: 16px;
      font-size: 28px;
      color: #ffba00;
      text-align: center;
    }

    .quiz-link {
      display: inline-block;
      margin-top: 10px;
      text-align: center;
      background-color: #ffc107;
      color: #000;
      padding: 12px 20px;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
    }

    @media (max-width: 768px) {
      iframe {
        height: 220px;
      }

      nav {
        flex-direction: column;
        align-items: stretch;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>رحلة المهندس المحترف</h1>
    <nav id="weekNav"></nav>
  </header>

  <div class="content" id="contentArea">
    <h2 id="lectureTitle">المحاضرات</h2>
    <div id="videos"></div>
    <a class="quiz-link" id="quizLink" href="#" target="_blank">الاختبار</a>
    <div class="locked-message" id="lockedMsg" style="display:none;">🔒 المحتوى غير متاح بعد. الرجاء العودة لاحقًا.</div>
  </div>

  <script>
    const startDate = new Date("2025-06-01T00:00:00Z"); // تاريخ أول دخول للمتدرب
    const now = new Date();
    const weekAvailable = Math.floor((now - startDate) / (7 * 24 * 60 * 60 * 1000)) + 1;
    const totalWeeks = 14;

    const lecturesData = Array.from({ length: totalWeeks }, (_, i) => ({
      title: `المحاضرات - الأسبوع ${i + 1}`,
      videos: [
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}&v=1`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}&v=2`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}&v=3`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}&v=4`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}&v=5`
      ],
      quiz: `https://example.com/quiz/week${i + 1}`
    }));

    const weekNav = document.getElementById("weekNav");
    const lectureTitle = document.getElementById("lectureTitle");
    const videos = document.getElementById("videos");
    const quizLink = document.getElementById("quizLink");
    const lockedMsg = document.getElementById("lockedMsg");

    function loadWeek(weekIndex) {
      videos.innerHTML = "";
      if (weekIndex >= weekAvailable) {
        lectureTitle.textContent = "محتوى غير متاح بعد";
        lockedMsg.style.display = "block";
        quizLink.style.display = "none";
        return;
      }

      const week = lecturesData[weekIndex];
      lectureTitle.textContent = week.title;
      lockedMsg.style.display = "none";

      week.videos.forEach(url => {
        const iframe = document.createElement("iframe");
        iframe.src = url;
        videos.appendChild(iframe);
      });

      quizLink.href = week.quiz;
      quizLink.style.display = "inline-block";
    }

    lecturesData.forEach((week, i) => {
      const btn = document.createElement("button");
      btn.textContent = `الأسبوع ${i + 1}`;
      btn.className = i < weekAvailable ? "" : "locked";
      btn.onclick = () => loadWeek(i);
      weekNav.appendChild(btn);
    });

    loadWeek(0);
  </script>
</body>
</html>
