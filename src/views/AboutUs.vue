<template>
  <div class="about-container">
    <nav class="navbar">
      <div class="nav-content">
        <h2>關於我們</h2>
        <div class="nav-links">
          <router-link to="/">回到登入</router-link>
          <router-link v-if="isLoggedIn" to="/welcome">歡迎頁面</router-link>
        </div>
      </div>
    </nav>
    <main class="main-content">
      <div class="about-card">
        <h1>關於我們</h1>
        <div class="about-section">
          <h2>公司簡介</h2>
          <p>
            我們是一家致力於提供優質服務的公司，專注於為客戶創造價值。
            透過創新的技術和專業的團隊，我們持續為客戶提供最佳的解決方案。
          </p>
        </div>
        <div class="about-section">
          <h2>我們的使命</h2>
          <p>
            以客戶為中心，提供創新且可靠的服務，協助客戶實現目標。
          </p>
        </div>
        <div class="about-section">
          <h2>聯絡方式</h2>
          <ul class="contact-list">
            <li><strong>電話:</strong> (02) 1234-5678</li>
            <li><strong>Email:</strong> info@example.com</li>
            <li><strong>地址:</strong> 台北市信義區信義路五段7號</li>
          </ul>
        </div>
        <div class="tech-info">
          <h3>技術資訊</h3>
          <p><strong>Context Path:</strong> {{ contextPath }}</p>
          <p><strong>環境模式:</strong> {{ mode }}</p>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'

const contextPath = ref('')
const mode = ref('')
const isLoggedIn = computed(() => localStorage.getItem('isLoggedIn') === 'true')

onMounted(() => {
  contextPath.value = import.meta.env.VITE_CONTEXT_PATH || '/'
  mode.value = import.meta.env.MODE
})
</script>

<style lang="scss" scoped>
.about-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);

  .navbar {
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1rem 0;

    .nav-content {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;

      h2 {
        margin: 0;
        color: #333;
      }

      .nav-links {
        display: flex;
        gap: 1rem;

        a {
          color: #667eea;
          text-decoration: none;
          padding: 0.5rem 1rem;
          border-radius: 5px;
          transition: background-color 0.3s;

          &:hover {
            background-color: #f0f0f0;
          }
        }
      }
    }
  }

  .main-content {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 2rem;

    .about-card {
      background: white;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

      h1 {
        color: #333;
        margin-bottom: 2rem;
        text-align: center;
      }

      .about-section {
        margin-bottom: 2rem;

        h2 {
          color: #667eea;
          margin-bottom: 1rem;
          font-size: 1.5rem;
        }

        p {
          color: #666;
          line-height: 1.8;
          text-align: justify;
        }

        .contact-list {
          list-style: none;
          padding: 0;

          li {
            color: #666;
            margin-bottom: 0.75rem;
            padding-left: 1.5rem;
            position: relative;

            &:before {
              content: "▸";
              position: absolute;
              left: 0;
              color: #667eea;
            }

            strong {
              color: #333;
            }
          }
        }
      }

      .tech-info {
        margin-top: 2rem;
        padding: 1.5rem;
        background: #f8f9fa;
        border-radius: 5px;
        border-left: 4px solid #fcb69f;

        h3 {
          color: #333;
          margin-bottom: 1rem;
        }

        p {
          margin: 0.5rem 0;
          color: #666;
          
          strong {
            color: #333;
          }
        }
      }
    }
  }
}
</style>
