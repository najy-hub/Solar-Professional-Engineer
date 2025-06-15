<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background: linear-gradient(to right, #0f0f0f, #1c1c1c);
      color: #ffffff;
      line-height: 1.6;
    }

    header {
      padding: 20px 40px;
      background-color: #111111d0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #333;
    }

    header h1 {
      font-size: 24px;
      color: #f9f9f9;
    }

    nav a {
      color: #ccc;
      text-decoration: none;
      margin-left: 20px;
      font-size: 16px;
      transition: color 0.3s;
    }

    nav a:hover {
      color: #ffffff;
    }

    .hero {
      position: relative;
      background-image: url('Images/hero.png');
      background-size: cover;
      background-position: center;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .hero::after {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-color: rgba(0,0,0,0.6);
      z-index: 1;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      padding: 20px;
    }

    .hero h2 {
      font-size: 36px;
      margin-bottom: 20px;
      color: #ffffff;
    }

    .hero p {
      font-size: 18px;
      color: #dddddd;
      margin-bottom: 30px;
    }

    .hero a.button {
      padding: 12px 30px;
      background-color: #ffba00;
      color: #000;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      text-decoration: none;
      font-size: 18px;
      transition: background-color 0.3s;
    }

    .hero a.button:hover {
      background-color: #ffaa00;
    }

    #video {
      padding: 60px 20px;
      text-align: center;
    }

    footer {
      background-color: #101010;
      text-align: center;
      padding: 20px;
      color: #666;
      font-size: 14px;
      margin-top: 60px;
    }

    @media (max-width: 768px) {
      .hero h2 {
        font-size: 28px;
      }

      .hero p {
        font-size: 16px;
      }

      header {
        flex-direction: column;
        align-items: flex-start;
      }

      nav {
        margin-top: 10px;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>رحلة المهندس المحترف</h1>
    <nav>
      <a href="#about">عن الدورة</a>
      <a href="#video">فيديو</a>
      <a href="#contact">تواصل معنا</a>
    </nav>
  </header>

  <section class="hero">
    <div class="hero-content">
      <h2>رحلتك تبدأ من هنا</h2>
      <p>دورة متكاملة لتعلم تصميم وتنفيذ أنظمة الطاقة الشمسية بطرق عملية وعلمية.</p>
      <a href="#video" class="button">شاهد المقدمة</a>
    </div>
  </section>

  <section id="video">
    <h2 style="margin-bottom: 20px;">🎥 المحاضرة</h2>
    <iframe width="800" height="450" 
      src="https://www.youtube.com/embed/zW9ZX-SZKtE" 
      frameborder="0" allowfullscreen 
      style="max-width: 100%; border-radius: 12px;">
    </iframe>
  </section>
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>قسم التعليقات</title>
  <style>
    body {
      background-color: #111;
      color: #fff;
      font-family: 'Cairo', sans-serif;
      padding: 40px 20px;
      max-width: 800px;
      margin: auto;
    }

    h2 {
      text-align: center;
      margin-bottom: 30px;
    }

    form {
      background: #1e1e1e;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 40px;
    }

    label {
      display: block;
      margin: 10px 0 5px;
    }

    input, textarea, select {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: none;
      border-radius: 8px;
      background: #2c2c2c;
      color: #fff;
    }

    button {
      background: #ffc107;
      color: #000;
      font-weight: bold;
      padding: 12px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background: #e0a800;
    }

    .comment {
      background: #1e1e1e;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .reply {
      margin-right: 20px;
      background: #262626;
    }

    .rating {
      color: gold;
    }

    .reply-button {
      font-size: 13px;
      color: #00c3ff;
      cursor: pointer;
      margin-top: 5px;
      display: inline-block;
    }

    .reply-form {
      display: none;
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <h2>💬 قسم التعليقات</h2>

  <form id="commentForm">
    <label>الاسم:</label>
    <input type="text" name="name" required>

    <label>البريد الإلكتروني (اختياري):</label>
    <input type="email" name="email">

    <label>التقييم:</label>
    <select name="rating">
      <option value="5">⭐️⭐️⭐️⭐️⭐️</option>
      <option value="4">⭐️⭐️⭐️⭐️</option>
      <option value="3">⭐️⭐️⭐️</option>
      <option value="2">⭐️⭐️</option>
      <option value="1">⭐️</option>
    </select>

    <label>التعليق:</label>
    <textarea name="comment" required></textarea>

    <input type="hidden" name="parentId" value="">
    <button type="submit">إرسال</button>
  </form>

  <div id="comments"></div>

  <script>
    const scriptURL = "https://script.google.com/macros/s/PASTE_YOUR_SCRIPT_URL_HERE/exec";

    document.getElementById("commentForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const form = e.target;
      const formData = new FormData(form);

      fetch(scriptURL, {
        method: 'POST',
        body: formData
      }).then(() => {
        alert("✅ تم إرسال التعليق");
        form.reset();
        loadComments();
      });
    });

    function createCommentHtml(comment, allComments) {
      const div = document.createElement("div");
      div.className = "comment" + (comment.parentId ? " reply" : "");
      div.innerHTML = `
        <strong>${comment.name}</strong>
        <div class="rating">⭐️ × ${comment.rating}</div>
        <p>${comment.comment}</p>
        ${!comment.parentId ? `<span class="reply-button" onclick="showReplyForm(${comment.id})">رد</span>` : ""}
        <form class="reply-form" id="replyForm-${comment.id}">
          <input type="text" name="name" placeholder="اسمك" required>
          <input type="email" name="email" placeholder="بريدك">
          <textarea name="comment" placeholder="ردك" required></textarea>
          <input type="hidden" name="rating" value="5">
          <input type="hidden" name="parentId" value="${comment.id}">
          <button type="submit">إرسال الرد</button>
        </form>
      `;

      div.querySelector("form")?.addEventListener("submit", function(e) {
        e.preventDefault();
        const replyForm = e.target;
        const replyData = new FormData(replyForm);

        fetch(scriptURL, {
          method: 'POST',
          body: replyData
        }).then(() => {
          alert("✅ تم إرسال الرد");
          loadComments();
        });
      });

      return div;
    }

    function loadComments() {
      fetch(scriptURL)
        .then(res => res.json())
        .then(data => {
          const commentSection = document.getElementById("comments");
          commentSection.innerHTML = "";
          const parents = data.filter(c => !c.parentId);
          const replies = data.filter(c => c.parentId);

          parents.forEach(parent => {
            const parentDiv = createCommentHtml(parent);
            commentSection.appendChild(parentDiv);

            replies.filter(r => r.parentId == parent.id).forEach(reply => {
              const replyDiv = createCommentHtml(reply);
              commentSection.appendChild(replyDiv);
            });
          });
        });
    }

    function showReplyForm(id) {
      document.getElementById(`replyForm-${id}`).style.display = 'block';
    }

    // تحميل التعليقات تلقائياً عند فتح الصفحة
    loadComments();
  </script>
</body>
</html>


  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>
<script>
  async function submitComment(event) {
    event.preventDefault();
    const form = document.getElementById('commentForm');
    const formData = new FormData(form);
    
    const data = {
      name: formData.get('name'),
      comment: formData.get('comment'),
      rating: formData.get('rating'),
    };

    await fetch('https://script.google.com/macros/s/AKfycbwMPaKP0nVZVkTZOc9y9cm_GdK5ILcFwIuQhYyPGNo0KfDXoqy9PYTH9d-c0UfADNKhSw/exec', {
      method: 'POST',
      mode: 'no-cors',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    });

    alert("✅ تم إرسال التعليق!");
    form.reset();
    loadComments(); // لتحديث القائمة
  }

  async function loadComments() {
    const response = await fetch('https://script.google.com/macros/s/AKfycbwMPaKP0nVZVkTZOc9y9cm_GdK5ILcFwIuQhYyPGNo0KfDXoqy9PYTH9d-c0UfADNKhSw/exec');
    const comments = await response.json();

    const container = document.getElementById('commentsContainer');
    container.innerHTML = '';

    comments.reverse().forEach(c => {
      const ratingStars = '⭐'.repeat(Number(c.rating));
      container.innerHTML += `
        <div style="background:#222; padding:15px; border-radius:10px; margin-bottom:15px;">
          <strong>${c.name}</strong> <span style="color:#ffba00;">${ratingStars}</span>
          <p>${c.comment}</p>
        </div>`;
    });
  }

  window.onload = loadComments;
</script>

</body>
</html>
