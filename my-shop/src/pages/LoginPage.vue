<template>
  <div>
    <h2>Авторизація</h2>

    <input 
      v-model="username" 
      placeholder="Логін"
    />

    <input 
      v-model="password" 
      type="password" 
      placeholder="Пароль"
    />

    <button v-on:click="login">
      Увійти
    </button>

    <p v-if="message">
      {{ message }}
    </p>
  </div>
</template>

<script>
export default {
  name: "LoginPage",
  data() {
    return {
      username: "",
      password: "",
      message: "",
      users: []
    };
  },
  methods: {
    login: function () {

      if (!this.username || !this.password) {
        this.message = "Введіть логін та пароль!";
        return;
      }

      const user = this.users.find(u =>
        u.username === this.username && u.password === this.password
      );

      if (user) {
        this.message = "Вхід успішний!";

        localStorage.setItem("authUser", this.username);

        this.$router.push("/profile");
      } else {
        this.message = "Невірний логін або пароль.";
      }
    }
  },
  async mounted() {
    try {
      const response = await fetch("/admin.json");
      if (!response.ok) {
        throw new Error("HTTP помилка: " + response.status);
      }
      this.users = await response.json();
    } catch (error) {
      console.error("Помилка завантаження JSON: " + error);
      this.message = "Помилка сервера! Спробуйте пізніше.";
    }
  }
};
</script>