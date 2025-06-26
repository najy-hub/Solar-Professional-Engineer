<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>رحلة المهندس المحترف - المحتوى</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0; padding: 0; box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background: linear-gradient(to right, #0f0f0f, #1c1c1c);
      color: #fff; display: flex; flex-direction: column;
      min-height: 100vh;
    }

    header {
      background: #111;
      padding: 20px;
      text-align: center;
      border-bottom: 1px solid #333;
    }

    header h1 {
      font-size: 24px;
    }

    .container {
      display: flex;
      flex: 1;
    }

    aside {
      width: 280px;
      background: #222;
      padding: 20px;
      overflow-y: auto;
    }

    .accordion {
      background-color: #333;
      color: #fff;
      cursor: pointer;
      padding: 15px;
      width: 100%;
      border: none;
      text-align: right;
      outline: none;
      font-size: 16px;
      transition: 0.3s;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    .accordion.active, .accordion:hover {
      background-color: #444;
    }

    .panel {
      padding: 0 15px;
      display: none;
      flex-direction: column;
      background-color: #2c2c2c;
      margin-bottom: 10px;
      border-radius: 0 0 8px 8px;
    }

    .video-button {
      background: none;
      color: #ffc107;
      padding: 10px;
      text-align: right;
      border: none;
      cursor: pointer;
      font-size: 15px;
      border-bottom: 1px solid #444;
    }

    .video-button:hover {
      color: #fff;
    }

    main {
      flex: 1;
      padding: 20px;
    }

    .video-container {
      max-width: 100%;
      height: auto;
    }

    iframe {
      width: 100%;
      height: 450px;
      border: none;
      border-radius: 12px;
    }

    .locked {
      opacity: 0.5;
      pointer-events: none;
    }

    .locked::after {
      content: '🔒 سيفتح لاحقًا';
      display: block;
      color: red;
      font-size: 14px;
      margin-top: 5px;
    }

    @media (max-width: 768px) {
      .container {
        flex-direction: column;
      }
      aside {
        width: 100%;
        order: 2;
      }
      main {
        order: 1;
      }
      iframe {
        height: 250px;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>رحلة المهندس المحترف - منصة المحتوى</h1>
  </header>

  <div class="container">
    <aside id="weeks">
      <!-- سيتم توليد القائمة تلقائياً -->
    </aside>
    <main>
      <h2 id="video-title">اختر محاضرة من القائمة</h2>
      <div class="video-container">
        <iframe id="video-frame" src="" allowfullscreen></iframe>
      </div>
    </main>
  </div>

  <script>
    const startDate = new Date("2024-06-01");
    const today = new Date();
    const msInDay = 1000 * 60 * 60 * 24;
    const daysPassed = Math.floor((today - startDate) / msInDay);
    const currentWeek = Math.min(Math.floor(daysPassed / 7) + 1, 14);

    const videoData = Array.from({ length: 14 }, (_, weekIdx) => ({
      week: weekIdx + 1,
      videos: Array.from({ length: 5 }, (_, vidIdx) => ({
        title: `📘 المحاضرة ${vidIdx + 1}`,
        url: `https://www.youtube.com/embed/dQw4w9WgXcQ`
      }))
    }));

    const weeksContainer = document.getElementById("weeks");

    videoData.forEach(({ week, videos }) => {
      const isUnlocked = week <= currentWeek;

      const accordion = document.createElement("button");
      accordion.className = "accordion" + (!isUnlocked ? " locked" : "");
      accordion.textContent = `الأسبوع ${week}`;

      const panel = document.createElement("div");
      panel.className = "panel";

      videos.forEach(video => {
        const btn = document.createElement("button");
        btn.className = "video-button";
        btn.textContent = video.title;
        btn.onclick = () => {
          document.getElementById("video-title").textContent = video.title;
          document.getElementById("video-frame").src = video.url;
        };
        panel.appendChild(btn);
      });

      accordion.onclick = function () {
        this.classList.toggle("active");
        const isOpen = panel.style.display === "flex";
        panel.style.display = isOpen ? "none" : "flex";
      };

      if (isUnlocked) {
        weeksContainer.appendChild(accordion);
        weeksContainer.appendChild(panel);
      } else {
        accordion.disabled = true;
        weeksContainer.appendChild(accordion);
      }
    });
  </script>

</body>
</html>
