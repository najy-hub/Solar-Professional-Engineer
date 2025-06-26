<!-- هذا مجرد تمهيد للهيكل العام. سيتم استكماله تدريجياً حسب الطلب -->

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>منصة رحلة المهندس - المحتوى الأسبوعي</title>
  <style>
    body { font-family: 'Cairo', sans-serif; background: #111; color: #fff; margin: 0; padding: 0; }
    header, footer { background: #1c1c1c; padding: 20px; text-align: center; }
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
