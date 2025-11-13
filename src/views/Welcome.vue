<template>
  <div class="welcome-container">
    <nav class="navbar">
      <div class="nav-content">
        <h2>歡迎頁面</h2>
        <div class="nav-links">
          <router-link to="/about">關於我們</router-link>
          <button @click="handleLogout" class="logout-btn">登出</button>
        </div>
      </div>
    </nav>
    <main class="main-content">
      <div class="welcome-card">
        <h1>歡迎回來，{{ username }}！</h1>
        <p>您已成功登入系統。</p>
        <div class="info-section">
          <h3>當前環境資訊</h3>
          <p><strong>Context Path:</strong> {{ contextPath }}</p>
          <p><strong>環境模式:</strong> {{ mode }}</p>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const username = ref('')
const contextPath = ref('')
const mode = ref('')

onMounted(() => {
  username.value = localStorage.getItem('username') || '訪客'
  contextPath.value = import.meta.env.VITE_CONTEXT_PATH || '/'
  mode.value = import.meta.env.MODE
})

const handleLogout = () => {
  localStorage.removeItem('isLoggedIn')
  localStorage.removeItem('username')
  router.push('/')
}
</script>

<style lang="scss" scoped>
.welcome-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);

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
        align-items: center;

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

        .logout-btn {
          padding: 0.5rem 1rem;
          background: #dc3545;
          color: white;
          border: none;
          border-radius: 5px;
          cursor: pointer;
          transition: background-color 0.3s;

          &:hover {
            background: #c82333;
          }
        }
      }
    }
  }

  .main-content {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 2rem;

    .welcome-card {
      background: white;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

      h1 {
        color: #333;
        margin-bottom: 1rem;
      }

      p {
        color: #666;
        line-height: 1.6;
      }

      .info-section {
        margin-top: 2rem;
        padding: 1.5rem;
        background: #f8f9fa;
        border-radius: 5px;
        border-left: 4px solid #667eea;

        h3 {
          color: #333;
          margin-bottom: 1rem;
        }

        p {
          margin: 0.5rem 0;
          
          strong {
            color: #333;
          }
        }
      }
    }
  }
}
</style>
