<template>
  <div>
    <div class="login">
      <form>
        <h1>Login form</h1>
        <input
          maxlength="16"
          type="text"
          placeholder="Username"
          v-model="userName"
          @keyup="checkvalidate"
        />
        <p :style="{ color: validateStyle ? 'red' : 'black' }">
          <i>
            Info: Don't use numbers, cyrillic symbols and any special characters
          </i>
        </p>
        <div class="login-btn">
          <button @click="checkvalidate">
            <nuxt-link :to="isValidate ? '/main' : ''">Log In</nuxt-link>
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isValidate: false,
      userName: "",
      validateStyle: false,
    };
  },
  methods: {
    checkvalidate() {
      let a = /[a-zA-Z]+/;

      if (a.test(this.userName)) {
        this.isValidate = true;
        this.validateStyle = false;
      } else {
        this.isValidate = false;
        this.validateStyle = true;
      }
    },
  },
};
</script>

<style scoped>
.login {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 200px;
  margin: 3rem auto;
  border: 1px solid;
  border-radius: 10px;
  padding: 3rem;
}
form {
  display: flex;
  justify-content: center;
  flex-direction: column;
}
h1 {
  text-align: center;
  font-family: sans-serif;
}

input {
  padding: 0.2rem 0.4rem;
  margin: 1rem 0 0;
}

.login-btn {
  margin: 3rem 0 0 0;
  text-align: center;
}

.login-btn a {
  text-decoration: none;
  color: white;
  background-image: linear-gradient(
    45deg,
    rgb(204, 204, 204),
    rgb(159, 159, 255)
  );
  padding: 0.6rem 2rem;
  cursor: pointer;
  border-radius: 15px;
}

button {
  border: none;
  background: transparent;
  font-size: 1.6rem;
}

p {
  text-align: center;
  font-size: 0.8rem;
}
</style>
