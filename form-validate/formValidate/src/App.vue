<template>
  <div class="validation">
    <form>
      <h2>Валидация формы</h2>

      <input class="validation-username" type="text" name="username" placeholder="Введите имя..." required />
      <input v-model="emailValue" @input="logEmail" class="validation-email" type="email" name="email" placeholder="email@example.com" required />
      <input class="validation-password" type="password" name="password" placeholder="password@example.com" required minlength="6" />

      <input class="validation-submit" type="submit" value="Войти">
    </form>
  </div>
</template>

<script>
export default {

  data() {
    return {
      emailValue: '',
    }
  },

  computed: {
    isEmailValid() {
      return this.checkEmail(this.emailValue);
    }
  },

  methods: {
    checkEmail(email) {
      let check = new RegExp(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/);
      return check.test(email);
    },
    logEmail() {
      console.log(this.checkEmail(this.emailValue));
    }
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

  .validation-submit {
    margin-top: auto;
    background-color: white;
    color: black;
  }
}
</style>