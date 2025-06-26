<!-- هذا مجرد تمهيد للهيكل العام. سيتم استكماله تدريجياً حسب الطلب -->

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>منصة رحلة المهندس - المحتوى الأسبوعي</title>
  <style>
    body { font-family: 'Cairo', sans-serif; background: #111; color: #fff; margin: 0; padding: 0; }
    header, footer { background: #1c1c<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>رحلة المهندس المحترف - المحتوى الأسبوعي</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #111;
      color: #fff;
      margin: 0;
      padding: 20px;
    }
    .dropdown {
      max-width: 600px;
      margin: auto;
      background: #1e1e1e;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.4);
    }
    select {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      background: #222;
      color: #fff;
      font-size: 16px;
      border: none;
    }
    .content {
      margin-top: 30px;
    }
    .locked {
      text-align: center;
      padding: 30px;
      background: #2c2c2c;
      border-radius: 10px;
      position: relative;
    }
    .locked::before {
      content: '\1F512'; /* رمز قفل */
      font-size: 40px;
      display: block;
      margin-bottom: 10px;
    }
    .video-container {
      margin-bottom: 20px;
    }
    iframe {
      width: 100%;
      height: 300px;
      border-radius: 10px;
      border: none;
    }
    h3 {
      margin-bottom: 10px;
      color: #ffc107;
    }
    .quiz-link {
      display: inline-block;
      margin-top: 20px;
      background: #ffc107;
      color: #000;
      padding: 10px 20px;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="dropdown">
    <h2>اختر الأسبوع</h2>
    <select id="weekSelect" onchange="showContent()">
      <option value="">-- اختر أسبوعاً --</option>
      <option value="1">الأسبوع الأول</option>
      <option value="2">الأسبوع الثاني</option>
      <option value="3">الأسبوع الثالث</option>
      <!-- أكمل حتى الأسبوع 14 -->
    </select>

    <div class="content" id="contentArea"></div>
  </div>

  <script>
    const firstLogin = localStorage.getItem('firstLoginDate') || (() => {
      const now = new Date();
      localStorage.setItem('firstLoginDate', now);
      return now;
    })();

    function weekAvailable(weekNumber) {
      const now = new Date();
      const loginDate = new Date(firstLogin);
      const diffInDays = Math.floor((now - loginDate) / (1000 * 60 * 60 * 24));
      return diffInDays >= (weekNumber - 1) * 7;
    }

    function showContent() {
      const week = parseInt(document.getElementById("weekSelect").value);
      const area = document.getElementById("contentArea");
      area.innerHTML = "";

      if (!week) return;

      if (!weekAvailable(week)) {
        area.innerHTML = `
          <div class="locked">
            <p>هذا الأسبوع لم يتم فتحه بعد. يرجى الرجوع لاحقًا.</p>
          </div>
        `;
        return;
      }

      // مثال لمحاضرات الأسبوع
      area.innerHTML = `
        <h3>محاضرات الأسبوع ${week}</h3>
        <div class="video-container">
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </div>
        <div class="video-container">
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </div>
        <div class="video-container">
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </div>
        <div class="video-container">
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </div>
        <div class="video-container">
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </div>
        <a class="quiz-link" href="#">الانتقال إلى اختبار الأسبوع</a>
      `;
    }
  </script>

</body>
</html>
1c; padding: 20px; text-align: center; }
    nav select {
      padding: 10px;
      margin: 20px auto;
      display: block;
      background: #222;
      color: #fff;
      border: 1px solid #444;
      border-radius: 6px;
    }
    .week-content { display: none; padding: 20px; }
    iframe { width: 100%; max-width: 800px; height: 400px; margin-bottom: 20px; border-radius: 10px; }
    .quiz { background: #1a1a1a; padding: 20px; border-radius: 10px; margin-top: 20px; }
  </style>
</head>
<body>
  <header>
    <h1>مرحبا بك في دورة رحلة المهندس المحترف</h1>
  </header>

  <nav>
    <select id="weekSelector" onchange="changeWeek()">
      <option value="">اختر الأسبوع</option>
      <!-- سيتم توليد 14 أسبوع -->
      <script>
        for (let i = 1; i <= 14; i++) {
          document.write(`<option value="week${i}">الأسبوع ${i}</option>`);
        }
      </script>
    </select>
  </nav>

  <!-- محتوى الأسابيع -->
  <main id="weeks">
    <!-- مثال على أسبوع 1، سيتم تكرار الشكل لبقية الأسابيع ديناميكيًا لاحقًا -->
    <div class="week-content" id="week1">
      <h2>الأسبوع 1</h2>
      <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
      <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
      <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
      <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
      <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>

      <div class="quiz">
        <h3>اختبار الأسبوع</h3>
        <p><a href="#">رابط الاختبار</a></p>
      </div>
    </div>

    <!-- سيتم تكرار بقية الأسابيع ديناميكيًا -->
  </main>

  <footer>
    جميع الحقوق محفوظة &copy; 2025
  </footer>

  <script>
    // تحديد أول دخول في الجلسة
    if (!localStorage.getItem("courseStartDate")) {
      localStorage.setItem("courseStartDate", new Date().toISOString());
    }

    function changeWeek() {
      const selected = document.getElementById("weekSelector").value;
      const allWeeks = document.querySelectorAll(".week-content");
      allWeeks.forEach(div => div.style.display = "none");

      if (selected) {
        const startDate = new Date(localStorage.getItem("courseStartDate"));
        const currentDate = new Date();
        const weekNumber = parseInt(selected.replace("week", ""));
        const allowedDate = new Date(startDate);
        allowedDate.setDate(startDate.getDate() + (weekNumber - 1) * 7);

        if (currentDate >= allowedDate) {
          document.getElementById(selected).style.display = "block";
        } else {
          alert("🕒 هذا الأسبوع لم يتم فتحه بعد. سيتم فتحه تلقائيًا في: " + allowedDate.toLocaleDateString());
        }
      }
    }
  </script>
</body>
</html>
