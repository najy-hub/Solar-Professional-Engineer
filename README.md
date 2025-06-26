<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>دروس الدورة</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #111;
      color: #fff;
      margin: 0;
      display: flex;
    }

    .sidebar {
      width: 300px;
      background-color: #1a1a1a;
      padding: 20px;
      height: 100vh;
      overflow-y: auto;
      position: fixed;
      right: 0;
      top: 0;
      border-left: 1px solid #333;
    }

    .accordion {
      background-color: #2a2a2a;
      color: #fff;
      cursor: pointer;
      padding: 12px;
      width: 100%;
      border: none;
      text-align: right;
      outline: none;
      font-size: 18px;
      margin-bottom: 8px;
      border-radius: 8px;
      transition: background 0.3s;
    }

    .accordion.locked {
      background-color: #444;
      cursor: not-allowed;
      position: relative;
    }

    .accordion.locked::after {
      content: '\1F512';
      position: absolute;
      left: 10px;
    }

    .panel {
      padding: 0 12px;
      display: none;
      background-color: #1f1f1f;
      border-radius: 0 0 8px 8px;
      margin-bottom: 10px;
    }

    .panel iframe {
      width: 100%;
      height: 250px;
      margin-bottom: 10px;
      border-radius: 8px;
      border: none;
    }

    .main-content {
      margin-right: 320px;
      padding: 20px;
    }

    .locked-message {
      color: #ff9800;
      font-size: 14px;
      margin-top: 5px;
    }
  </style>
</head>
<body>

  <div class="sidebar" id="weeksList">
    <!-- سيتم توليد الأسابيع هنا -->
  </div>

  <div class="main-content">
    <h1>🎓 المحتوى التدريبي</h1>
    <p>اختر أحد الأسابيع من القائمة اليمنى.</p>
  </div>

  <script>
    const userStartDate = new Date("2025-06-01T00:00:00"); // تاريخ أول دخول للمتدرب
    const today = new Date();
    const weeksContainer = document.getElementById("weeksList");

    for (let week = 1; week <= 14; week++) {
      const weekOpenDate = new Date(userStartDate);
      weekOpenDate.setDate(userStartDate.getDate() + (week - 1) * 7);
      const isOpen = today >= weekOpenDate;

      const button = document.createElement("button");
      button.className = "accordion" + (isOpen ? "" : " locked");
      button.innerHTML = `الأسبوع ${week}`;

      const panel = document.createElement("div");
      panel.className = "panel";

      if (isOpen) {
        for (let v = 1; v <= 5; v++) {
          const iframe = document.createElement("iframe");
          iframe.src = `https://www.youtube.com/embed/VIDEO_ID_WEEK${week}_VID${v}`;
          iframe.title = `محاضرة ${v}`;
          panel.appendChild(iframe);
        }
      } else {
        const lockedMsg = document.createElement("div");
        lockedMsg.className = "locked-message";
        lockedMsg.textContent = "🚫 سيتم فتح هذا الأسبوع لاحقًا حسب الجدول.";
        panel.appendChild(lockedMsg);
      }

      button.onclick = function() {
        if (!isOpen) return;
        this.classList.toggle("active");
        panel.style.display = panel.style.display === "block" ? "none" : "block";
      };

      weeksContainer.appendChild(button);
      weeksContainer.appendChild(panel);
    }
  </script>

</body>
</html>
