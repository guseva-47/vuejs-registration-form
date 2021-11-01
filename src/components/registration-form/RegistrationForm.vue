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
    <form class="registration-body" action="#" method="post" autocomplete="on">
      <div class="registration-body__line">
        <form-line
          :params="paramsOfInput.name"
          :value="data.name"
          @update:value="updateName"
        />
      </div>
      <div class="registration-body__line">
        <form-line
          :params="paramsOfInput.email"
          :value="data.email"
          @update:value="updateEmail"
          @forBlur="onEmailBlur"
        />
      </div>
      <div class="registration-body__line">
        <form-line
          :params="paramsOfInput.phone"
          :value="data.phone"
          @update:value="updatePhone"
          @forBlur="onPhoneBlur"
        />
      </div>

      <div class="registration-body__line registration-body__select">
        <label :for="selectId" class="registration-body__label label">
          Язык
        </label>
        <v-select
          :options="languages"
          @choose="onChooseLang"
          placeholder="Язык"
          :optionsMaxHeight="selectOptionsMaxHeight"
        />
      </div>

      <div class="registration-body__line registration-body__accept-rules">
        <label class="label">
          <input
            class="checkbox"
            type="checkbox"
            v-model="data.isAcceptRules"
          />
          Принимаю
          <a href="#" class="link">условия</a> использования
        </label>
      </div>

      <div class="registration-body__line">
        <button
          class="button"
          type="button"
          :disabled="!isInputCompleted"
          @click="registrationRequest"
        >
          Зарегистрироваться
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import FormLine from "./FormLine.vue";
import VSelect from "./VSelect.vue";

export default {
  name: "RegistrationForm",
  components: {
    FormLine,
    VSelect,
  },
  data() {
    return {
      selectId: "selectId1",

      data: {
        name: "",
        email: "",
        phone: "",
        language: "",
        isAcceptRules: false,
      },

      paramsOfInput: {
        name: {},
        email: {},
        phone: {},
      },

      languages: [
        "Русский",
        "Английский",
        "Китайский",
        "Испанский",
        "Французский",
        "Немецкий",
      ],

      needValidCheck: {
        email: false,
        phone: false,
      },

      selectOptionsMaxHeight: 191,
    };
  },
  created() {
    this.paramsOfInput.name = this.initParams(
      "reg-name",
      "Имя",
      "text",
      "Введите Ваше имя"
    );
    this.paramsOfInput.email = this.initParams(
      "reg-email",
      "Email",
      "email",
      "Введите ваш email"
    );
    this.paramsOfInput.phone = this.initParams(
      "reg-number",
      "Номер телефона",
      "tel",
      "Введите номер телефона"
    );
  },
  computed: {
    // - поле “Имя” не может содержать цифры и символы кроме пробела и дефиса
    nameIsValid() {
      const myRe = /^([a-zа-яё]+)((\s?|-?)[a-zа-яё]+)*$/i;
      return myRe.test(this.data.name);
    },

    // - в поле “email” можно отправить только email.
    emailIsValid() {
      if (!this.needValidCheck.email) return true;

      const myRe = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return myRe.test(this.data.email);
    },

    // - в поле “номер телефона” можно ввести только 11 цифр, круглые скобки, дефис и знак плюс.
    phoneIsValid() {
      if (!this.needValidCheck.phone) return true;
      const validSymbols = /^([-()+\d])+$/;
      if (!validSymbols.test(this.data.phone)) return false;

      const numbers = this.data.phone
        .split("")
        .filter((n) => Number.isInteger(Number(n)));

      const DIGIT_COUNT = 11;
      return DIGIT_COUNT === numbers.length;
    },

    // чек, что все поля заполнены, причем валидными данными
    isInputCompleted() {
      let isComleted =
        Object.values(this.data).findIndex((inpData) => !inpData) === -1;

      isComleted =
        isComleted &&
        this.nameIsValid &&
        this.emailIsValid &&
        this.phoneIsValid;

      return isComleted;
    },
  },
  methods: {
    initParams(id, label, type, placeholder, isValid = true) {
      return {
        id: id ?? `${new Date(0)}`,
        label: label ?? "",
        type: type ?? "text",
        placeholder: placeholder ?? "",
        isValid: isValid ?? true,
      };
    },

    onChooseLang(option) {
      this.data.language = option;
    },

    // обработка события "снятие фокуса из поля ввода form-line".
    onPhoneBlur(value) {
      // считаем, что пользователь закончил ввод данных, 
      //  значит пора начинать валидацию, она не будет раздражающе преждевременной
      this.needValidCheck.phone = true;
      this.updatePhone(value);
    },

    // обработка события "снятие фокуса из поля ввода form-line".
    onEmailBlur(value) {
      // считаем, что пользователь закончил ввод данных, 
      //  значит пора начинать валидацию, она не будет раздражающе преждевременной
      this.needValidCheck.email = true;
      this.updateEmail(value);
    },

    updateName(value) {
      this.data.name = value;
      this.paramsOfInput.name.isValid = this.nameIsValid;
    },

    updateEmail(email) {
      this.data.email = email;
      this.paramsOfInput.email.isValid = this.emailIsValid;
    },

    updatePhone(phone) {
      this.data.phone = phone;
      this.paramsOfInput.phone.isValid = this.phoneIsValid;
    },

    // заглушка для отправки данных формы
    async registrationRequest() {
      if (!this.isInputCompleted) {
        console.log("Some entered data are not valid.");
        return;
      }

      const data = {
        name: this.data.name,
        email: this.data.email,
        phone: this.data.phone,
        language: this.data.language,
        isAcceptRules: this.data.isAcceptRules,
      };

      data.phone = this.data.phone
        .split("")
        .filter((n) => Number.isInteger(Number(n)));

      console.log(data);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;700&display=swap");

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

.registration-body__line + .registration-body__line {
  margin-top: 8px;
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

.registration-body__select {
  display: flex;
  flex-direction: column;
  margin-bottom: 34px;
}

.registration-body__label {
  margin: 0 0 8px 0;
}

.registration-body__accept-rules {
  display: block;
  line-height: 28px;
  margin-bottom: 37px;
}
</style>
