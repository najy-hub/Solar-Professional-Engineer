<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>دورة رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Cairo', sans-serif;
    }

    body {
      display: flex;
      background-color: #111;
      color: #fff;
      min-height: 100vh;
    }

    .sidebar {
      width: 250px;
      background-color: #1a1a1a;
      padding: 20px;
      border-left: 4px solid #ffc107;
      overflow-y: auto;
    }

    .sidebar h2 {
      font-size: 20px;
      margin-bottom: 20px;
      color: #ffc107;
    }

    .accordion {
      background-color: #222;
      border: none;
      color: #fff;
      padding: 15px;
      text-align: right;
      width: 100%;
      outline: none;
      font-size: 16px;
      border-radius: 8px;
      margin-bottom: 10px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .accordion:hover {
      background-color: #333;
    }

    .accordion.locked {
      background-color: #444;
      color: #999;
      cursor: not-allowed;
    }

    .accordion.locked::after {
      content: '🔒';
      float: left;
    }

    .panel {
      padding: 0 15px;
      display: none;
      flex-direction: column;
      background-color: #1f1f1f;
      border-radius: 8px;
      margin-bottom: 20px;
    }

    .panel iframe {
      margin: 15px 0;
      border-radius: 8px;
      width: 100%;
      max-width: 700px;
      height: 400px;
    }

    .panel h3 {
      margin: 10px 0;
      font-size: 18px;
      color: #ffba00;
    }

    .content {
      flex: 1;
      padding: 40px;
    }

    .locked-message {
      background-color: #333;
      color: #ff6666;
      padding: 10px;
      border-radius: 6px;
      margin-top: 10px;
    }

    @media (max-width: 768px) {
      body {
        flex-direction: column;
      }
      .sidebar {
        width: 100%;
        border-left: none;
        border-bottom: 4px solid #ffc107;
      }
    }
  </style>
</head>
<body>
  <div class="sidebar">
    <h2>أسابيع الدورة</h2>
    <div id="accordionContainer"></div>
  </div>

  <div class="content">
    <h1>مرحبًا بك في الدورة التدريبية</h1>
    <p>اختر الأسبوع من القائمة لعرض المحاضرات الخاصة به.</p>
  </div>

  <script>
    const userStartDate = new Date(localStorage.getItem("startDate") || new Date());
    localStorage.setItem("startDate", userStartDate);

    const weeksData = Array.from({ length: 14 }, (_, i) => ({
      title: `الأسبوع ${i + 1}`,
      videos: [
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}-1`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}-2`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}-3`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}-4`,
        `https://www.youtube.com/embed/zW9ZX-SZKtE?week=${i+1}-5`
      ]
    }));

    const accordionContainer = document.getElementById("accordionContainer");

    weeksData.forEach((week, index) => {
      const daysSinceStart = (new Date() - new Date(userStartDate)) / (1000 * 60 * 60 * 24);
      const isUnlocked = daysSinceStart >= (index * 7);

      const btn = document.createElement("button");
      btn.className = "accordion" + (isUnlocked ? "" : " locked");
      btn.textContent = week.title;

      const panel = document.createElement("div");
      panel.className = "panel";

      if (!isUnlocked) {
        const lockedMsg = document.createElement("div");
        lockedMsg.className = "locked-message";
        lockedMsg.textContent = "هذا الأسبوع غير متاح بعد. الرجاء العودة لاحقًا.";
        panel.appendChild(lockedMsg);
      } else {
        week.videos.forEach((vid, i) => {
          const title = document.createElement("h3");
          title.textContent = `محاضرة ${i + 1}`;
          const iframe = document.createElement("iframe");
          iframe.src = vid;
          iframe.allowFullscreen = true;
          panel.appendChild(title);
          panel.appendChild(iframe);
        });
      }

      btn.addEventListener("click", function () {
        if (!isUnlocked) return;
        this.classList.toggle("active");
        panel.style.display = panel.style.display === "flex" ? "none" : "flex";
      });

      accordionContainer.appendChild(btn);
      accordionContainer.appendChild(panel);
    });
  </script>
</body>
</html>
