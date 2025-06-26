<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>رحلة المهندس المحترف - محتوى الدورة</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; font-family: 'Cairo', sans-serif; }
    body {
      margin: 0; background-color: #121212; color: #fff; display: flex;
    }
    .sidebar {
      width: 260px; background: #1f1f1f; padding: 20px; height: 100vh;
      position: fixed; overflow-y: auto; border-left: 1px solid #333;
    }
    .sidebar h2 { font-size: 20px; color: #ffba00; margin-bottom: 20px; }
    .week-link {
      padding: 10px; margin-bottom: 10px; border-radius: 8px;
      background-color: #2a2a2a; text-decoration: none; color: #fff;
      display: flex; justify-content: space-between; align-items: center;
      transition: background 0.3s;
    }
    .week-link:hover { background-color: #383838; }
    .locked { opacity: 0.6; cursor: not-allowed; }
    .main-content {
      margin-right: 280px; padding: 30px; flex: 1;
    }
    .video-block {
      margin-bottom: 40px;
    }
    .video-title { margin-bottom: 10px; font-weight: bold; font-size: 18px; color: #ffba00; }
    iframe { width: 100%; height: 400px; border-radius: 12px; border: none; }
    .locked-msg {
      text-align: center; padding: 60px; font-size: 18px;
      background-color: #222; border-radius: 12px; border: 1px dashed #ffba00;
    }
  </style>
</head>
<body>
  <div class="sidebar">
    <h2>الأسابيع</h2>
    <div id="weekList"></div>
  </div>

  <div class="main-content" id="mainContent">
    <div class="locked-msg" id="lockedMessage">🔒 المحتوى غير متاح حاليًا. سيتم فتحه بعد مرور أسبوع من تاريخ التسجيل.</div>
  </div>

  <script>
    const firstLoginDate = new Date(localStorage.getItem('firstLogin')) || new Date();
    if (!localStorage.getItem('firstLogin')) {
      localStorage.setItem('firstLogin', firstLoginDate);
    }

    const weekData = Array.from({ length: 14 }, (_, i) => ({
      week: i + 1,
      videos: [
        { title: "محاضرة 1", url: "https://www.youtube.com/embed/zW9ZX-SZKtE" },
        { title: "محاضرة 2", url: "https://www.youtube.com/embed/zW9ZX-SZKtE" },
        { title: "محاضرة 3", url: "https://www.youtube.com/embed/zW9ZX-SZKtE" },
        { title: "محاضرة 4", url: "https://www.youtube.com/embed/zW9ZX-SZKtE" },
        { title: "محاضرة 5", url: "https://www.youtube.com/embed/zW9ZX-SZKtE" }
      ]
    }));

    const weekList = document.getElementById('weekList');
    const mainContent = document.getElementById('mainContent');
    const now = new Date();

    weekData.forEach(({ week }, index) => {
      const weekAvailable = now - new Date(firstLoginDate) >= index * 7 * 24 * 60 * 60 * 1000;
      const link = document.createElement('a');
      link.className = 'week-link' + (weekAvailable ? '' : ' locked');
      link.href = '#';
      link.innerHTML = `الأسبوع ${week} ${!weekAvailable ? '<span>🔒</span>' : ''}`;
      link.onclick = (e) => {
        e.preventDefault();
        if (!weekAvailable) return;
        renderWeek(week);
      };
      weekList.appendChild(link);
    });

    function renderWeek(weekNum) {
      const week = weekData.find(w => w.week === weekNum);
      mainContent.innerHTML = `<h2>الأسبوع ${weekNum}</h2>`;
      week.videos.forEach(video => {
        const block = document.createElement('div');
        block.className = 'video-block';
        block.innerHTML = `
          <div class="video-title">🎥 ${video.title}</div>
          <iframe src="${video.url}" allowfullscreen></iframe>
        `;
        mainContent.appendChild(block);
      });
    }
  </script>
</body>
</html>
