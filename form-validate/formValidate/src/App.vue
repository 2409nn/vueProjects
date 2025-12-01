<template>
  <div class="validation">
    <form>
      <h2>Валидация формы</h2>

      <input
          class="validation-username"
          v-model="usernameValue"
          type="text" name="username" placeholder="Введите имя..." required />
      <input
          :class="{ valid: isEmailValid, invalid: !isEmailValid && emailValue !== '' }"
          v-model="emailValue"
          class="validation-email"
          type="email" name="email" placeholder="email@example.com" required />
      <input v-model="passwordValue" class="validation-password" type="password" name="password" placeholder="password@example.com" required minlength="6" />

      <input
          :class="{ available: isFormValid }"
          @click:p.prevent=""
          :disabled="!isFormValid"
          class="validation-submit" type="submit" value="Войти">
    </form>
  </div>
</template>

<script>
export default {

  data() {
    return {
      emailValue: '',
      passwordValue: '',
      usernameValue: '',

    }
  },

  computed: {
    isEmailValid() {
      return this.checkEmail(this.emailValue);
    },
    isFormValid() {
      return this.isEmailValid
          && this.emailValue.length > 0
          && this.passwordValue.length > 6
          && this.usernameValue.length > 0
    }
  },

  methods: {
    checkEmail(email) {
      let check = new RegExp(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/);
      return check.test(email);
    },
  }
}
</script>

<style lang="scss" scoped>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

* {
  font-family: 'montserrat', 'sans-serif';
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

.validation {
  form {
    display: flex;
    flex-direction: column;

    width: 500px;
    height: 600px;
    background: #1f66f3;
    border: 1px solid #1f66f3;
    padding: 20px 5px;
  }

  h2 {
    text-align: center;
    color: white;
    padding-bottom: 40px;
  }

  input {
    padding: 20px;
    font-size: 16px;
    border: none;
    margin: 2px;
    outline: none;
  }

  input.invalid {
    box-shadow: 0 0 0 3px #ff5151 inset;
  }

  .validation-submit {
    margin-top: auto;
    background-color: #a2a2a2;
    color: black;
    cursor: not-allowed;
  }

  .available {
    background-color: white;
    cursor: pointer;
  }
}
</style>