<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="contact">
        <h3>Контакти</h3>
        <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
        <p>Телефон: <a href="tel:+380501234567">+38 050 123 45 67</a></p>
      </div>
      <div class="links">
        <h3>Корисні посилання</h3>
        <ul>
          <li><a href="#">Про нас</a></li>
          <li><a href="#">Доставка</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      &copy; 2025 Ваш сайт. Всі права захищені.
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent'
}
</script>

<style scoped>
.footer {
  background-color: #f8f8f8;
  color: #333;
  padding: 20px 0;
  font-family: Arial, sans-serif;
  margin-top: auto;
}

.footer-content {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.contact, .links {
  margin-bottom: 15px;
}

.contact h3, .links h3 {
  margin-bottom: 10px;
  font-size: 18px;
}

.links ul {
  list-style: none;
  padding: 0;
}

.links li {
  margin-bottom: 5px;
}

.links a, .contact a {
  color: #007BFF;
  text-decoration: none;
}

.links a:hover, .contact a:hover {
  text-decoration: underline;
}

.footer-bottom {
  text-align: center;
  margin-top: 15px;
  font-size: 14px;
  color: #666;
}
</style>
