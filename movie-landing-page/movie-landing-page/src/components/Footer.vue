<template>
  <footer class="site-footer">
    <div class="footer-content">
      <!-- Left: Title + Address -->
      <div class="footer-info">
        <h3 class="footer-title">Logoipsum</h3>
        <p class="footer-address">
          Port City, Colombo,<br />
          Sri Lanka
        </p>
      </div>

      <!-- Right: Social Icons -->
      <div class="footer-socials">
        <a href="https://twitter.com" target="_blank" aria-label="Twitter">
          <img src="/assets/Icons/Twitter White.svg" alt="Twitter" />
        </a>
        <a href="https://www.youtube.com" target="_blank" aria-label="YouTube">
          <img src="/assets/Icons/Youtube White.svg" alt="YouTube" />
        </a>
      </div>
    </div>

    <!-- Bottom: Copyright -->
    <div class="footer-bottom">
      <p>© {{ year }} Logoipsum. All rights reserved.</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      year: new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
.site-footer {
  background: #111;
  color: #fff;
  padding: 40px 20px 20px;
  font-family: Arial, sans-serif;
}
.footer-content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}
.footer-info {
  margin-bottom: 20px;
}
.footer-title {
  margin: 0 0 8px;
  font-size: 1.5rem;
}
.footer-address {
  margin: 0;
  line-height: 1.4;
  font-size: 1rem;
}
.footer-socials a {
  margin-left: 12px;
  display: inline-block;
}
.footer-socials img {
  width: 24px;
  height: 24px;
  display: block;
}
.footer-bottom {
  text-align: center;
  margin-top: 30px;
  font-size: 0.875rem;
  border-top: 1px solid #333;
  padding-top: 12px;
}
@media (max-width: 600px) {
  .footer-content {
    flex-direction: column;
    text-align: center;
  }
  .footer-socials {
    margin-top: 16px;
  }
}
</style>