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
      position: relative;
    }

    #logoutBtn {
      position: absolute;
      left: 20px;
      top: 20px;
      background: #e53935;
      color: #fff;
      border: none;
      padding: 8px 16px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
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

    #progressBar {
      width: 90%;
      max-width: 600px;
      margin: 20px auto;
      background: #333;
      border-radius: 10px;
      overflow: hidden;
      height: 20px;
    }

    #progressBarInner {
      height: 100%;
      background: #ffc107;
      width: 0%;
      transition: width 0.5s ease-in-out;
    }

    .expand-btn {
      display: block;
      margin: 10px auto;
      padding: 6px 12px;
      font-size: 14px;
      background: #444;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    .week-navigation {
      text-align: center;
      margin: 20px auto;
    }

    .week-navigation button {
      padding: 10px 20px;
      margin: 0 10px;
      background: #ffc107;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      color: #000;
    }

    .category-nav {
      display: flex;
      justify-content: center;
      margin-top: 10px;
      gap: 20px;
    }

    .category-nav button {
      background: #444;
      color: #fff;
      border: none;
      padding: 8px 16px;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
    }

    .category-nav button:hover {
      background: #666;
    }

    @media (max-width: 768px) {
      iframe {
        height: 250px;
      }

      .video-item h4 {
        font-size: 16px;
        text-align: center;
      }

      .category-nav {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>
  <script>
    // التحقق من الدخول
    if (localStorage.getItem("loggedIn") !== "true") {
      window.location.href = "https://najy-hub.github.io/Login-Course/";
    }
  </script>

  <header>
    <h1>مرحبا بك في دورة رحلة المهندس المحترف</h1>
    <button id="logoutBtn" onclick="logout()">🚪 تسجيل الخروج</button>
  </header>

  <div class="category-nav">
    <button onclick="jumpToCategory('Basic')">🧱 Basic</button>
    <button onclick="jumpToCategory('Professional')">🚀 Professional</button>
  </div>

  <div id="progressBar">
    <div id="progressBarInner"></div>
  </div>

  <main id="weeks"></main>

  <div class="week-navigation">
    <button onclick="navigateWeek(-1)">⬅️ السابق</button>
    <button onclick="navigateWeek(1)">التالي ➡️</button>
  </div>

  <footer>
    جميع الحقوق محفوظة &copy; 2025
  </footer>

  <script>
    function logout() {
      localStorage.removeItem("loggedIn");
      localStorage.removeItem("courseStartDate");
      window.location.href = "https://najy-hub.github.io/Login-Course/";
    }

    if (!localStorage.getItem("courseStartDate")) {
      localStorage.setItem("courseStartDate", new Date().toISOString());
    }

    const weeksContainer = document.getElementById("weeks");
    let currentWeek = null;
    const categoryIndexes = { Basic: 1, Professional: 8 };

    for (let i = 1; i <= 14; i++) {
      const weekDiv = document.createElement("div");
      weekDiv.className = "week-content";
      weekDiv.id = `week${i}`;

      const type = i <= 7 ? 'Basic' : 'Professional';
      const startDate = new Date(localStorage.getItem("courseStartDate"));
      const allowedDate = new Date(startDate);
      allowedDate.setDate(startDate.getDate() + (i - 1) * 7);
      const currentDate = new Date();

      const title = document.createElement("h2");
      title.textContent = `الأسبوع ${i} - ${type}`;

      if (currentDate < allowedDate) {
        title.innerHTML += " 🔒";
      } else {
        title.innerHTML += " ✅";
      }
 const ul = document.createElement("ul");
      ul.className = "video-list";
      for (let j = 1; j <= 5; j++) {
        const li = document.createElement("li");
        li.className = "video-item";
        li.innerHTML = `
          <h4>📘 المحاضرة ${j}</h4>
          <iframe src="https://www.youtube.com/embed/zW9ZX-SZKtE" allowfullscreen loading="lazy"></iframe>
          <button class="expand-btn" onclick="expandVideo(this)">🔍 توسيع الفيديو</button>
        `;
        ul.appendChild(li);
      }
      const videoData = {};
const quizLinks = {};
const videoData = {
  1: [
    { title: "محاضرة 1: مقدمة في الطاقة الشمسية", url: "https://www.youtube.com/embed/VID11" },
    { title: "محاضرة 2: مكونات النظام الشمسي", url: "https://www.youtube.com/embed/VID12" },
    { title: "محاضرة 3: أنواع الألواح الشمسية", url: "https://www.youtube.com/embed/VID13" },
    { title: "محاضرة 4: تركيب الأنظمة", url: "https://www.youtube.com/embed/VID14" },
    { title: "محاضرة 5: تصميم النظام الشمسي", url: "https://www.youtube.com/embed/VID15" }
  ],
  2: [
    { title: "محاضرة 6: البطاريات وأنواعها", url: "https://www.youtube.com/embed/VID21" },
    { title: "محاضرة 7: أنظمة الشحن", url: "https://www.youtube.com/embed/VID22" },
    { title: "محاضرة 8: BMS وكيف يعمل", url: "https://www.youtube.com/embed/VID23" },
    { title: "محاضرة 9: التوصيلات والحماية", url: "https://www.youtube.com/embed/VID24" },
    { title: "محاضرة 10: موازنة الأنظمة", url: "https://www.youtube.com/embed/VID25" }
  ],
  // كرر بنفس الطريقة حتى الأسبوع 14
};

          <button class="expand-btn" onclick="expandVideo(this)">🔍 توسيع الفيديو</button>
        `;
        ul.appendChild(li);
      }

      const quiz = document.createElement("div");
      quiz.className = "quiz";
      quiz.innerHTML = `<h3>📝 اختبار الأسبوع</h3><p><a href="#">رابط الاختبار</a></p>`;

      weekDiv.appendChild(title);
      weekDiv.appendChild(ul);
      weekDiv.appendChild(quiz);
      weeksContainer.appendChild(weekDiv);
    }

    function updateProgressBar() {
      const startDate = new Date(localStorage.getItem("courseStartDate"));
      const currentDate = new Date();
      const diffInDays = Math.floor((currentDate - startDate) / (1000 * 60 * 60 * 24));
      const weekUnlocked = Math.min(14, Math.floor(diffInDays / 7) + 1);
      const percentage = (weekUnlocked / 14) * 100;
      document.getElementById("progressBarInner").style.width = `${percentage}%`;
    }

    function changeWeekId(weekNumber) {
      const allWeeks = document.querySelectorAll(".week-content");
      allWeeks.forEach(div => div.style.display = "none");

      const startDate = new Date(localStorage.getItem("courseStartDate"));
      const currentDate = new Date();
      const allowedDate = new Date(startDate);
      allowedDate.setDate(startDate.getDate() + (weekNumber - 1) * 7);

      if (currentDate >= allowedDate) {
        document.getElementById(`week${weekNumber}`).style.display = "block";
        currentWeek = weekNumber;
      } else {
        alert("🔒 هذا الأسبوع لم يتم فتحه بعد. سيتم فتحه تلقائيًا في: " + allowedDate.toLocaleDateString());
      }
    }

    function navigateWeek(step) {
      if (currentWeek === null) return;
      const nextWeek = currentWeek + step;
      if (nextWeek >= 1 && nextWeek <= 14) {
        changeWeekId(nextWeek);
      }
    }

    function expandVideo(button) {
      const iframe = button.previousElementSibling;
      if (iframe.style.width !== "100vw") {
        iframe.style.width = "100vw";
        iframe.style.height = "90vh";
        iframe.style.position = "fixed";
        iframe.style.top = "5vh";
        iframe.style.left = "0";
        iframe.style.zIndex = "9999";
        iframe.style.borderRadius = "0";
        button.textContent = "❌ إغلاق الفيديو";
      } else {
        iframe.removeAttribute("style");
        button.textContent = "🔍 توسيع الفيديو";
      }
    }

    function jumpToCategory(category) {
      const week = categoryIndexes[category];
      changeWeekId(week);
    }

    changeWeekId(1);
    updateProgressBar();
  </script>
</body>
</html>
