<template>
  <div class="registration">
    <div class="registration-header">
      <h1 class="registration-header__title title">Регистрация</h1>
      <h2 class="registration-header__subtitle">
        Уже есть аккаунт<a href="#" class="registration-header__link link"
          >Войти</a
        >
      </h2>
    </div>
    <div class="registration-body">
      <form
        class="registration-body__form"
        action="#"
        method="post"
        autocomplete="on"
      >
        <!-- TODO v-for для полей -->
        <div class="registration-body__input">
          <FormLine
            inputId="reg-name"
            inputLabel="Имя"
            inputType="text"
            inputPlaceholder="Введите Ваше имя"
          />
        </div>
        <div class="registration-body__input">
          <FormLine
            inputId="reg-email"
            inputLabel="Email"
            inputType="email"
            inputPlaceholder="Введите ваш email"
          />
        </div>
        <div class="registration-body__input">
          <FormLine
            inputId="reg-number"
            inputLabel="Номер телефона"
            inputType="tel"
            inputPlaceholder="Введите номер телефона"
          />
        </div>
        <!-- TODO вынести -->
        <div class="registration-body__select">
          <label :for="selectId" class="registration-body__label label">Язык</label>
          <select class="select" v-model="language" :placeholder="Язык" :id="selectId">
            <option disabled value="">Язык</option>
            <option>А пррп прдад оридлоидоидл ридлоидлои доидлоидли</option>
            <option>Б</option>
          </select>
        </div>

        <!-- TODO вынести ????????????? -->
        <div class="accept-line registration-body__input">
          <label class="accept-line__label label">
            <input
              class="accept-line__checkbox checkbox"
              type="checkbox"
              v-model="toggle"
            />
            Принимаю
            <a href="#" class="accept-line__link link">условия</a> использования
          </label>
        </div>

        <!-- TODO вынести -->
        <div class="registration-button">
          <button class="button" type="button" :disabled="true">
            Зарегистрироваться
          </button>
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

/* 
  TODO
  отдельный класс для инпута
    класс для чекбокса
    класс для лейбела
    ?класс для лебел ссылки
    класс для кнопки
 */
.title {
  font-style: normal;
  font-weight: bold;
  font-size: 34px;
  line-height: 44px;
}

.link {
  color: #0880ae;
}

.registration {
  font-family: "IBM Plex Sans", sans-serif;
  font-size: 16px;
  line-height: 22px;
  font-style: normal;
  font-weight: normal;

  width: 100%;
  min-width: 360px;
  padding: 40px 30px;
  border-radius: 24px;

  background-color: rgb(255, 255, 255);

  display: flex;
  flex-direction: column;
}

.registration-header {
  padding-bottom: 54px;
}

.registration-header__title {
  margin: 0 0 8px 0;
}

.registration-header__subtitle {
  display: block;
  line-height: 26px;
}

.registration-header__link {
  margin-left: 6px;
}

.registration-body {
}

.registration-body__form {
  /* display: flex;
  flex-direction: column; */
}

.registration-body__input + .registration-body__input {
  margin-top: 8px;
}

.registration-body__select {
  display: flex;
  flex-direction: column;
  margin-bottom: 34px;
}

.registration-body__label {
  margin: 0 0 8px 0;
}
.registration-button {
  display: block;
}

.accept-line {
  display: block;
  line-height: 28px;
  margin-bottom: 37px;
}

.accept-line__label {
  /* color: #756f86; */
}

.accept-line__link {
  /* color: #0880ae; */
}

/* ---- Button ---- */
.button {
  background: #0880ae;
  box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08),
    0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius: 6px;

  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 21px;
  /* identical to box height */

  text-align: center;

  color: #ebf4f8;

  width: 100%;
  padding: 18px 0 17px 0;
}
.button:hover {
  background: #0880ae;
}
.button:active {
  border: 2px solid rgba(106, 100, 119, 0.86);
  box-sizing: border-box;
  box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.0001),
    0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius: 6px;
  padding: 16px 0 15px 0;
}
.button:disabled {
  background: #dbe2ea;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius: 6px;

  color: #2c2738;

  mix-blend-mode: normal;
  opacity: 0.5;
}
/* ----------------- */

/* ---- Checkbox ---- */
.checkbox {
  -webkit-appearance: none;
  -moz-appearance: none;
  display: inline-block;
  width: 28px;
  height: 28px;
  padding: 0;
  vertical-align: top;
  outline: none;
  cursor: pointer;

  background: #ffffff;
  border: 1px solid #dbe2ea;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 4px;
}
.checkbox:checked {
  background: #ffffff;
  border: 2px solid #0880ae;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 4px;

  background-image: url("C:/Users/gusev/Documents/program/hello-work/amigoweb-registration-form/src/assets/Check.svg");
  background-size: 24px;
}
.checkbox:disabled {
  color: #666;
  cursor: default;
}
.checkbox:disabled {
  filter: grayscale(100%);
  opacity: 0.6;
}
/* .checkbox:focus {
  box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
} */

/* .checkbox:hover {
  filter: brightness(110%);
} */

/* .checkbox:active {
  filter: brightness(80%);
} */
/* ------------------- */

/* ---- Input ---- */
.input {
  display: block;
  background: #ffffff;
  border: 1px solid #dbe2ea;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 6px;

  padding: 15px 15px 14px 15px;

  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 21px;

  color: #2c2738;

  /* width: 100%; */
}
.input::placeholder {
  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 21px;

  color: #7c9cbf;
}
/* --------------- */

/* ---- Select ---- */

.select {
  display: block;
  background: #ffffff;
  border: 1px solid #dbe2ea;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 6px;

  background-image: url("C:/Users/gusev/Documents/program/hello-work/amigoweb-registration-form/src/assets/Chevron Bottom.svg");
  background-size: 30px;
  background-repeat: no-repeat, repeat;
  background-position: right 11px center;

  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;

  padding: 15px 15px 14px 15px;

  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 21px;

  color: #2c2738;
}
.select::-ms-expand {
  display: none;
}
.select:hover {
  border: 2px solid #0880ae;
  padding: 14px 14px 13px 14px;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
}
.select:focus {
  border: 2px solid #0880ae;
  padding: 14px 14px 13px 14px;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
}
*[dir="rtl"] .select,
:root:lang(ar) .select,
:root:lang(iw) .select {
  background-position: left 0.7em top 50%, 0 0;
  padding: 0.6em 0.8em 0.5em 1.4em;
}
/* ---------------- */
/* ---- Label ---- */
.label {
  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 21px;
  height: 20px;

  color: #756f86;
}
/* --------------- */
</style>
