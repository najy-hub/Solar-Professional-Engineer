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

    .bunny-video-container {
      width: 100%;
      max-width: 100%;
      aspect-ratio: 16 / 9;
      border-radius: 12px;
      overflow: hidden;
      background: #000;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 20px 0;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      border: 1px solid #ccc;
    }

    .bunny-video-container iframe {
      width: 100%;
      height: 100%;
      border: none;
      display: block;
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
      flex-wrap: wrap;
      margin-top: 10px;
      gap: 10px;
    }

    .category-nav button {
      background: #444;
      color: #fff;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
    }

    .category-nav button:hover {
      background: #666;
    }

    @media (max-width: 768px) {
      header h1 {
        font-size: 20px;
      }

      .video-item h4 {
        font-size: 16px;
        text-align: center;
      }

      .category-nav {
        flex-direction: column;
        align-items: center;
      }

      #logoutBtn {
        position: static;
        margin-top: 10px;
        display: block;
      }

      .week-navigation button {
        width: 100%;
        margin: 10px 0;
      }
    }
  </style>
</head>
<body>
  <script>
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

    const videoData = [
      [
        { title: "📘 المحاضرة 1", url: "https://iframe.mediadelivery.net/embed/460802/dce4ee28-5099-44df-9760-dddcf3609a95" },
        { title: "📘 انواع الالواح ", url: "https://iframe.mediadelivery.net/embed/460802/5c9229c6-4dc8-45cf-9b71-e6e4fce12da6" },
        { title: "📘 المحاضرة 3", url: "https://iframe.mediadelivery.net/embed/460802/7082d1ef-61a6-4ee4-82c0-ced096b8188f" },
        { title: "📘 المحاضرة 4", url: "https://iframe.mediadelivery.net/embed/460802/4b7a1509-496d-4d39-ba3c-d635198fa551" },
        { title: "📘 المحاضرة 5", url: "https://iframe.mediadelivery.net/embed/460802/cfe04177-caf9-4e6c-a873-9691897b0fc8" }
      ],
      [
        { title: "📘 المحاضرة 1", url: "https://www.youtube.com/embed/vid6" },
        { title: "📘 المحاضرة 2", url: "https://www.youtube.com/embed/mNPXseyrxMU" },
        { title: "📘 المحاضرة 3", url: "https://www.youtube.com/embed/vid8" },
        { title: "📘 المحاضرة 4", url: "https://www.youtube.com/embed/vid9" },
        { title: "📘 المحاضرة 5", url: "https://www.youtube.com/embed/vid10" }
      ]
    ];

    for (let i = 1; i <= videoData.length; i++) {
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
      videoData[i - 1].forEach(video => {
        const li = document.createElement("li");
        li.className = "video-item";
    li.innerHTML = `
  <h4>${video.title}</h4>
  <div class="bunny-video-container">
    <iframe src="${video.url}" allowfullscreen loading="lazy"></iframe>
  </div>
`;

        ul.appendChild(li);
      });

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
  const weekUnlocked = Math.min(14, Math.ceil((diffInDays + 1) / 7)); // أضف 1 حتى يبدأ من اليوم الأول
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
    if (currentWeek !== null) {
      document.getElementById(`week${currentWeek}`).style.display = "block";
    }
  }
}


    function navigateWeek(step) {
      if (currentWeek === null) return;
      const nextWeek = currentWeek + step;
      if (nextWeek >= 1 && nextWeek <= videoData.length) {
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
