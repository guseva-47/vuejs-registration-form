<template>
  <div class="registration">
    <div class="header">
      <h1 class="header__title">Регистрация</h1>
      <h2 class="header__subtitle">
        Уже есть аккаунт <a href="#" class="subtitle__link">Войти</a>
      </h2>
    </div>
    <div class="body">
      <form class="body__form" action="#" method="post" autocomplete="on">
        <!-- TODO v-for для полей -->
        <FormLine
          inputId="reg-name"
          inputLabel="Имя"
          inputType="text"
          inputPlaceholder="Введите Ваше имя"
        />
        <FormLine
          inputId="reg-email"
          inputLabel="Email"
          inputType="email"
          inputPlaceholder="Введите ваш email"
        />
        <FormLine
          inputId="reg-number"
          inputLabel="Номер телефона"
          inputType="tel"
          inputPlaceholder="Введите номер телефона"
        />
        <!-- TODO вынести -->
        <div id="v-model-select" class="demo">
          <select v-model="language" :placeholder="Язык">
            <option disabled value="">Язык</option>
            <option>А</option>
            <option>Б</option>
          </select>
        </div>
        <!-- TODO вынести -->
        <div class="terms-of-use">
          <input
            class="terms-of-use__checkbox checkbox"
            type="checkbox"
            v-model="toggle"
            id="terms-of-use__checkbox"
          />
          <label for="terms-of-use__checkbox" class="terms-of-use__label"
            >Принимаю
            <a href="#" class="terms-of-use__link">условия</a>
            использования</label
          >
        </div>
        <!-- TODO вынести -->
        <div class="registration-button">
          <button class="button" :disabled="true">Зарегистрироваться</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import FormLine from "./FormLine.vue";

export default {
  name: "RegistrationForm",
  components: {
    FormLine,
  },
  data() {
    return {
      language: "",
      toggle: false,
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;700&display=swap");

.registration {
  min-width: 360px;
  font-family: "IBM Plex Sans", sans-serif;
}
</style>
