<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>كورس الطاقة الشمسية - رحلة 14 أسبوع</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #f9f9f9;
      padding: 20px;
      color: #333;
    }
    h1 {
      text-align: center;
      color: #005b4f;
    }
    .week {
      margin-bottom: 20px;
      border: 1px solid #ccc;
      border-radius: 12px;
      background: #fff;
      padding: 15px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .week h2 {
      font-size: 20px;
      margin-bottom: 10px;
      color: #007b7f;
    }
    .lecture {
      margin: 10px 0;
    }
    iframe {
      width: 100%;
      height: 315px;
      border-radius: 10px;
      margin-top: 5px;
    }
    .locked {
      opacity: 0.4;
      pointer-events: none;
    }
  </style>
</head>
<body>

<h1>كورس الطاقة الشمسية</h1>
<p style="text-align: center;">يتكون هذا الكورس من 14 أسبوعًا، كل أسبوع يحتوي على 5 محاضرات. يتم فتح المحتوى تدريجيًا كل أسبوع.</p>

<div id="course-content"></div>

<script>
  const startDate = new Date("2025-07-01"); // 📅 عدل إلى تاريخ بداية الكورس
  const totalWeeks = 14;
  const lecturesPerWeek = 5;
  const today = new Date();
  const courseContent = document.getElementById("course-content");

  for (let week = 1; week <= totalWeeks; week++) {
    const weekStart = new Date(startDate);
    weekStart.setDate(startDate.getDate() + (week - 1) * 7);

    const isUnlocked = today >= weekStart;
    const weekDiv = document.createElement("div");
    weekDiv.className = `week ${isUnlocked ? "" : "locked"}`;
    weekDiv.innerHTML = `<h2>الأسبوع ${week}</h2>`;

    for (let lecture = 1; lecture <= lecturesPerWeek; lecture++) {
      const lectureNumber = (week - 1) * lecturesPerWeek + lecture;
      const bunnyId = `video${lectureNumber}`; // ✳️ غير هذا إلى ID الحقيقي إن توفر
      const videoUrl = `https://iframe.mediadelivery.net/embed/YOUR-BUNNY-STREAM-ID-HERE/${bunnyId}?autoplay=false`;

      weekDiv.innerHTML += `
        <div class="lecture">
          <strong>محاضرة ${lecture}:</strong>
          <iframe loading="lazy" src="${videoUrl}" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture;" allowfullscreen></iframe>
        </div>
      `;
    }

    courseContent.appendChild(weekDiv);
  }
</script>

</body>
</html>
