<script setup>
</script>

<template>
  <form @submit="submitLogin">
    <div class="container">
      <div class="content">
        <h1>Log in</h1>
        <div class="email">
          <!-- <label>Username: </label> -->
          <input type="email" placeholder="Email" name="email" v-model="form.email" required />
        </div>
        <div class="password">
          <!-- <label>Password: </label> -->
          <input
            type="password"
            placeholder="Password"
            name="password"
            v-model="form.password"
            required
          />
        </div>
        <button type="submit">Login</button>
      </div>
    </div>
  </form>
  <p>{{ form.email }}</p>
  <p>{{ form.password }}</p>
</template>

<script>
export default {
  data() {
    return {
      form: {
        email: "",
        password: "",
      }
    }
  },
  methods: {
    async submitLogin(e) {
      e.preventDefault();
      const result = await fetch('https://dev.beauty-at-home.it/api/login', {
        method: 'POST',
        mode: 'cors',
        body: JSON.stringify({
          email: this.form.email,
          password: this.form.password,
        })
      });
      return result;
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.content {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 400px;
  width: 100%;
}

h1 {
  font-weight: bold;
  text-align: center;
  font-size: 50px;
}

.content input {
  width: 100%;
  height: 40px;
  border-radius: 12px;
  border: 1px solid #c4c4c4;
  padding: 10px;
}

button {
  height: 40px;
  background: black;
  border: none;
  border-radius: 12px;
  color: white;
  font-weight: bold;
}
</style>
