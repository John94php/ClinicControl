<template>
  <div class="login">
    <h2>Logowanie</h2>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="email">Email:</label>
        <input type="email" v-model="email" required />
      </div>
      <div>
        <label for="password">Hasło:</label>
        <input type="password" v-model="password" required />
      </div>
      <button type="submit">Zaloguj</button>
    </form>
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      error: "",
    };
  },
  methods: {
    async handleSubmit() {
      try {
        const response = await fetch("/token", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            username: this.email,
            password: this.password,
          }),
        });
        if (!response.ok) {
          throw new Error("Nieprawidłowe dane logowania");
        }
        const data = await response.json();
        localStorage.setItem("token", data.access_token);
        this.$router.push("/dashboard"); // Przekierowanie po zalogowaniu
      } catch (error) {
        this.error = error.message;
      }
    },
  },
};
</script>

<style scoped>
.login {
  max-width: 300px;
  margin: 0 auto;
  padding: 1em;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.login div {
  margin-bottom: 1em;
}
.login label {
  display: block;
  margin-bottom: 0.5em;
}
.login input {
  width: 100%;
  padding: 0.5em;
  box-sizing: border-box;
}
</style>
