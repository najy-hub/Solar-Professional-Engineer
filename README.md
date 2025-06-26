<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #111;
      color: #fff;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #1c1c1c;
      padding: 20px;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
    }
    .container {
      display: flex;
      flex-direction: row;
      padding: 20px;
    }
    .accordion {
      width: 30%;
      margin-left: 20px;
    }
    .accordion-item {
      background-color: #222;
      border-radius: 8px;
      margin-bottom: 10px;
      overflow: hidden;
    }
    .accordion-header {
      padding: 15px;
      cursor: pointer;
      background-color: #333;
    }
    .accordion-header:hover {
      background-color: #444;
    }
    .accordion-body {
      display: none;
      padding: 15px;
      background-color: #2a2a2a;
    }
    .accordion-body button {
      display: block;
      width: 100%;
      margin: 5px 0;
      padding: 10px;
      background-color: #444;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
    .accordion-body button:hover {
      background-color: #555;
    }
    .video-player {
      flex: 1;
      padding: 0 20px;
    }
    iframe {
      width: 100%;
      height: 400px;
      border-radius: 12px;
      border: none;
    }
  </style>
</head>
<body>
  <header>رحلة المهندس المحترف</header>
  <div class="container">
    <div class="accordion" id="weekList">
      <!-- الأسابيع تظهر هنا -->
    </div>
    <div class="video-player">
      <h2 id="video-title">حدد فيديو لعرضه</h2>
      <iframe id="main-video" src="" allowfullscreen></iframe>
    </div>
  </div>

  <script>
    const weeks = 14;
    const videosPerWeek = 5;
    const firstAccess = new Date(localStorage.getItem('firstAccess') || new Date());
    localStorage.setItem('firstAccess', firstAccess);

    const weekList = document.getElementById('weekList');
    const videoFrame = document.getElementById('main-video');
    const videoTitle = document.getElementById('video-title');

    const videoLinks = {
      1: [
        { title: "مقدمة الأسبوع 1", link: "https://www.youtube.com/embed/zW9ZX-SZKtE" },
        { title: "الدرس 2", link: "https://www.youtube.com/embed/video2" },
        { title: "الدرس 3", link: "https://www.youtube.com/embed/video3" },
        { title: "الدرس 4", link: "https://www.youtube.com/embed/video4" },
        { title: "اختبار الأسبوع", link: "https://www.youtube.com/embed/quiz1" },
      ],
      // باقي الأسابيع يتم تعبئتها بنفس الطريقة
    };

    for (let i = 1; i <= weeks; i++) {
      const now = new Date();
      const availableDate = new Date(firstAccess);
      availableDate.setDate(availableDate.getDate() + (i - 1) * 7);

      const item = document.createElement("div");
      item.className = "accordion-item";

      const header = document.createElement("div");
      header.className = "accordion-header";
      header.textContent = `الأسبوع ${i}`;

      const body = document.createElement("div");
      body.className = "accordion-body";

      if (now >= availableDate && videoLinks[i]) {
        videoLinks[i].forEach(video => {
          const btn = document.createElement("button");
          btn.textContent = video.title;
          btn.onclick = () => {
            videoFrame.src = video.link;
            videoTitle.textContent = video.title;
          };
          body.appendChild(btn);
        });
      } else {
        const msg = document.createElement("div");
        msg.innerHTML = "🔒 سيتم فتح هذا الأسبوع قريبًا.";
        msg.style.padding = "10px";
        body.appendChild(msg);
      }

      header.onclick = () => {
        body.style.display = (body.style.display === "block") ? "none" : "block";
      };

      item.appendChild(header);
      item.appendChild(body);
      weekList.appendChild(item);
    }
  </script>
</body>
</html>
