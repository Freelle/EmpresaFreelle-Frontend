<script setup>
import { ref } from "vue";
import { useAuthStore } from "@/stores";
import { useRouter } from "vue-router";

const email = ref('')
const authStore = useAuthStore()
const router = useRouter()

const forgotPassword = async () => {
  try {
    await authStore.ForgotPasswordEmpresa(email.value)
    router.push('/reset-password')
  } catch (error) {
    console.error(error)
  }
}
</script>

<template>
  <div class="wrapContainer">
    <div class="FormTop">
      <img src="https://i.ibb.co/Qk43Z1V/icon-freelle-empresa.png" alt="Logo" class="logo" />
    </div>
    <div class="containerPrincipal">
      <div class="FormBot">
        <form @submit.prevent="forgotPassword" class="wrapForm">
          <h4 class="Text">Esqueceu sua senha?</h4>

          <div class="input-container">
            <input
              type="email"
              id="email"
              class="inputForm"
              v-model="email"
              required
            />
            <label for="email" class="labelForm" :class="{ 'active': email }">Digite seu email</label>
          </div>

          <button type="submit" class="btnCriar mt-3">Enviar Código</button>
          <p class="mt-4 FormP Pf">Protegido por reCAPTCHA - Privacidade | Condições</p>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
body {
  background: #00546B;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  color: white;
  font-family: 'Arial', sans-serif;
}

.wrapContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background: #00546B;
  padding-top: 20px;
}

.containerPrincipal {
  width: 440px;
  background-color: white;
  padding: 40px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  text-align: center;
}

.logo {
  width: 80px;
}

.Text {
  font-size: 18px;
}

.input-container {
  position: relative;
  margin-top: 30px;
}

.inputForm {
  width: 100%;
  height: 50px;
  padding: 15px;
  border: 1px solid #00546B;
  outline: none;
  transition: all 0.3s;
}

.inputForm:focus + .labelForm,
.labelForm.active {
  top: -10px;
  font-size: 12px;
  color: #00546B;
}

.labelForm {
  position: absolute;
  top: 50%;
  left: 15px;
  transform: translateY(-50%);
  transition: all 0.3s;
  pointer-events: none;
  color: #666;
}

.btnCriar {
  width: 100%;
  height: 45px;
  margin-top: 18px;
  font-size: 18px;
  font-weight: bold;
  background-color: white;
  border: 2px solid #00546B;
  color: #00546B;
  transition: all 0.3s ease;
}

.btnCriar:hover {
  background-color: #00546B;
  color: white;
}

.Pf {
  font-size: 12px;
  margin-top: 30px;
}

.footer {
  background: #00546B;
}

@media (max-width: 768px) {
  .containerPrincipal {
    width: 90%;
    padding: 20px;
  }

  .btnCriar {
    font-size: 16px;
    height: 40px;
  }

  .logo {
    width: 140px;
  }
}

@media (max-width: 576px) {
  .containerPrincipal {
    width: 80%;
    padding: 15px;
  }

  .inputForm {
    height: 40px;
    padding: 10px;
  }

  .btnCriar {
    height: 35px;
    font-size: 14px;
  }
}
</style>