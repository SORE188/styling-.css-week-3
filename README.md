<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>Easy Med</title>
  <style>
    /* Reset some default browser styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Basic Layout */
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      color: #333;
    }

    header {
      background: #5cb85c;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header .logo img {
      width: 50px;
      vertical-align: middle;
    }

    nav {
      background: #333;
      color: white;
    }

    .nav-links {
      list-style: none;
      display: flex;
      justify-content: space-around;
    }

    .nav-links a {
      color: white;
      text-decoration: none;
      padding: 15px;
      display: block;
    }

    .hamburger {
      display: none;
      flex-direction: column;
      cursor: pointer;
    }

    .hamburger span {
      height: 4px;
      background: white;
      margin: 4px 0;
      width: 25px;
    }

    .main-container {
      display: flex;
      padding: 20px;
    }

    /* Main content section */
    main {
      flex: 3;
      padding-right: 20px;
    }

    aside {
      flex: 1;
      background: #f4f4f4;
      padding: 10px;
    }

    aside .search-bar {
      margin-bottom: 20px;
    }

    aside .sidebar-links {
      list-style: none;
    }

    .sidebar-links li {
      margin-bottom: 10px;
    }

    footer {
      background: #333;
      color: white;
      padding: 20px;
      text-align: center;
    }

    footer .social-media {
      list-style: none;
      display: flex;
      justify-content: center;
    }

    footer .social-media li {
      margin: 0 10px;
    }

    footer .social-media a {
      color: white;
      text-decoration: none;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
      .main-container {
        flex-direction: column;
      }

      aside {
        margin-top: 20px;
      }
    }

    @media (max-width: 600px) {
      .nav-links {
        display: none;
        flex-direction: column;
      }

      .hamburger {
        display: flex;
        margin-right: 20px;
      }

      .nav-links.active {
        display: flex;
        position: absolute;
        top: 60px;
        right: 0;
        background: #333;
        width: 100%;
        height: 100vh;
        flex-direction: column;
        justify-content: center;
        align-items: center;
      }

      .nav-links a {
        font-size: 24px;
        padding: 20px;
      }
    }
  </style>
</head>
<body>
  <!-- Header Section -->
  <header>
    <div class="logo">
      <!-- Placeholder for Medical Snake Logo in Blue -->
      <img src="data:image/jpeg;base64,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IBBAOc+PQKfvOs23e0VEGnIhPUSRObJFIeGRjSNy1mMP9jt0TW1no6ey2rhhhknNbCySoETWulBBznhA5rg7SbLRWRlHeLQ1tHVCcN4YtgTgkOA8MY/K04vZJeya1pGTXMX486VN/bs3yTyF9fcrB2aWOps1lkdWxuinqZOMxO5saBgZ8+Zx5q3rxpJXTU0UrxwufG1xHQkZXssHUTOmldI/iVpRMEbA1vBERFCpEREREREREREREREREREREREREUXqO00d5tU1NXktiA4xIOcZH1BSi8quFtTSzQPJDZWFhI6EYXcbix4cDVLlzQ5pBWOcF7dYqN1HWtrrS2tjZSiaMscJAcNHzD9OdtnEDyU1QUZ1DqtlPqxtTDXUzO8ZRucHQyjn8uOQ6jfOOexC/E1TU2S0UFkvNHJG2jr4ZGVjBmKSMSZJJ8Dz2VhtFPU3nVn9IZYPh6KCn7il+drzMCSePLcjG58V9DPMWsc6gB3qcKvlXDjfPF+Syo4wSG5PCx66clbwMcl9RF82tdERERERERERERERERERERERERERERF8PJfURFRrrTRuvFZJUNDqo3Kh7sO3PccTAMDpxcefNTmlIWwNubKYAURrnmmA/SGlreLh/wAvHx4Xdd6GOugia6FkjmTxOHEAcAPaT+AV3NaGgBoAAGAAOStyaneiDfWK9fFQNi3X365r6iIqinREREREREREREREREREREREREREREREREREREREREREREREREREREREREX/2Q==" alt="Medical Image" style="width: 100px; height: auto;"" alt="Medical Snake Logo" style="color:blue;">
    </div>
    <h1>Easy Med</h1>
  </header>

  <!-- Navigation Bar -->
  <nav>
    <ul class="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <!-- Hamburger Menu for Mobile -->
    <div class="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </nav>

  <!-- Main Content and Sidebar Section -->
  <div class="main-container">
    <!-- Main Content Section -->
    <main>
      <section id="home">
        <h2>Welcome to Easy Med</h2>
        <p>Telemedicine allows you to consult with healthcare professionals from the comfort of your home. We offer a variety of services to meet your healthcare needs.</p>
      </section>

      <section id="services">
        <h2>Our Services</h2>
        <p>We offer virtual consultations, prescription refills, and remote monitoring.</p>
      </section>
    </main>

    <!-- Sidebar Section -->
    <aside>
      <div class="search-bar">
        <input type="text" placeholder="Search...">
        <button>Search</button>
      </div>
      <ul class="sidebar-links">
        <li><a href="#">Health Tips</a></li>
        <li><a href="#">Doctors Near You</a></li>
        <li><a href="#">Emergency Contacts</a></li>
      </ul>
    </aside>
  </div>

  <!-- Footer Section -->
  <footer>
    <p>&copy; 2024 Easy Med. All rights reserved.</p>
    <ul class="social-media">
      <li><a href="#">Facebook</a></li>
      <li><a href="#">Twitter</a></li>
      <li><a href="#">LinkedIn</a></li>
    </ul>
    <p>Contact us: info@easymed.com</p>
  </footer>

  <script>
    const hamburger = document.querySelector('.hamburger');
    const navLinks = document.querySelector('.nav-links');

    hamburger.addEventListener('click', () => {
      navLinks.classList.toggle('active');
    });
  </script>
</body>
</html># styling-.css-week-3
