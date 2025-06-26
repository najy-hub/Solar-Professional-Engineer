<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>منصة رحلة المهندس - المحتوى الأسبوعي</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background: #111;
      color: #fff;
      margin: 0;
      padding: 0;
    }

    header, footer {
      background: #1c1c1c;
      padding: 20px;
      text-align: center;
    }

    .category-label {
      font-size: 20px;
      margin: 20px;
      color: #ffc107;
    }

    nav .select-group {
      margin: 0 auto 30px auto;
      text-align: center;
    }

    nav select {
      padding: 10px;
      margin: 10px;
      background: #222;
      color: #fff;
      border: 1px solid #444;
      border-radius: 6px;
    }

    .week-content {
      display: none;
      padding: 20px;
    }

    .video-list {
      list-style: none;
      padding: 0;
    }

    .video-item {
      margin-bottom: 30px;
      background: #1a1a1a;
      border-radius: 10px;
      padding: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }

    .video-item h4 {
      margin-bottom: 10px;
      font-size: 18px;
      color: #ffca28;
    }

    iframe {
      width: 100%;
      max-width: 800px;
      height: 400px;
      border-radius: 10px;
      border: none;
      display: block;
      margin: auto;
    }

    .quiz {
      background: #1a1a1a;
      padding: 20px;
      border-radius: 10px;
      margin-top: 20px;
    }

    .quiz a {
      color: #ffc107;
      text-decoration: none;
    }

    .quiz a:hover {
      text-decoration: underline;
    }

    @media (max-width: 768px) {
      iframe {
        height: 250px;
      }

      .video-item h4 {
        font-size: 16px;
        text-align: center;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>مرحبا بك في دورة رحلة المهندس المحترف</h1>
  </header>

  <nav>
    <div class="select-group">
      <div class="category-label">Basic</div>
      <select onchange="changeWeek(this.value)">
        <option value="">اختر الأسبوع</option>
        <option value="week1">الأسبوع 1</option>
        <option value="week2">الأسبوع 2</option>
        <option value="week3">الأسبوع 3</option>
        <option value="week4">الأسبوع 4</option>
        <option value="week5">الأسبوع 5</option>
        <option value="week6">الأسبوع 6</option>
        <option value="week7">الأسبوع 7</option>
      </select>
    </div>
    <div class="select-group">
      <div class="category-label">Professional</div>
      <select onchange="changeWeek(this.value)">
        <option value="">اختر الأسبوع</option>
        <option value="week8">الأسبوع 8</option>
        <option value="week9">الأسبوع 9</option>
        <option value="week10">الأسبوع 10</option>
        <option value="week11">الأسبوع 11</option>
        <option value="week12">الأسبوع 12</option>
        <option value="week13">الأسبوع 13</option>
        <option value="week14">الأسبوع 14</option>
      </select>
    </div>
  </nav>

  <main id="weeks">
    <div class="week-content" id="week1">
      <h2>الأسبوع 1 - Basic</h2>
      <ul class="video-list">
        <li class="video-item">
          <h4>📘 المحاضرة الأولى: مقدمة الدورة</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </li>
        <li class="video-item">
          <h4>📘 المحاضرة الثانية: المفاهيم الأساسية</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </li>
        <li class="video-item">
          <h4>📘 المحاضرة الثالثة: مكونات النظام</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </li>
        <li class="video-item">
          <h4>📘 المحاضرة الرابعة: أنواع الأنظمة</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </li>
        <li class="video-item">
          <h4>📘 المحاضرة الخامسة: الحسابات الأساسية</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen></iframe>
        </li>
      </ul>

      <div class="quiz">
        <h3>📝 اختبار الأسبوع</h3>
        <p><a href="#">رابط الاختبار</a></p>
      </div>
    </div>
  </main>

  <footer>
    جميع الحقوق محفوظة &copy; 2025
  </footer>

  <script>
    if (!localStorage.getItem("courseStartDate")) {
      localStorage.setItem("courseStartDate", new Date().toISOString());
    }

    function changeWeek(weekId) {
      const allWeeks = document.querySelectorAll(".week-content");
      allWeeks.forEach(div => div.style.display = "none");

      if (weekId) {
        const startDate = new Date(localStorage.getItem("courseStartDate"));
        const currentDate = new Date();
        const weekNumber = parseInt(weekId.replace("week", ""));
        const allowedDate = new Date(startDate);
        allowedDate.setDate(startDate.getDate() + (weekNumber - 1) * 7);

        if (currentDate >= allowedDate) {
          document.getElementById(weekId).style.display = "block";
        } else {
          alert("🕒 هذا الأسبوع لم يتم فتحه بعد. سيتم فتحه تلقائيًا في: " + allowedDate.toLocaleDateString());
        }
      }
    }
  </script>
</body>
</html>
