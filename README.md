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

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

</body>
</html>
