<template>
  <div class="wrapper">
    <registration-form />
  </div>
</template>

<script>
import RegistrationForm from "./components/registration-form/RegistrationForm.vue";

export default {
  name: "App",
  components: {
    RegistrationForm,
  },
};
</script>

<style>
/* Обнуление стандартных стилей */
* {
  padding: 0;
  margin: 0;
  border: 0;
}
*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
:focus,
:active {
  outline: none;
}
a:focus,
a:active {
  outline: none;
}

nav,
footer,
header,
aside {
  display: block;
}

html,
body {
  height: 100%;
  width: 100%;
  font-size: 100%;
  line-height: 1;
  font-size: 14px;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
input,
button,
textarea {
  font-family: inherit;
}

input::-ms-clear {
  display: none;
}
button {
  cursor: pointer;
}
button::-moz-focus-inner {
  padding: 0;
  border: 0;
}
a,
a:visited {
  text-decoration: none;
}
a:hover {
  text-decoration: none;
}
ul li {
  list-style: none;
}
img {
  vertical-align: top;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: 400;
}
/*--------------------*/
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;700&display=swap");

.wrapper {
  min-height: 100%;
  overflow: hidden;
}

.title {
  font-family: "IBM Plex Sans", sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 34px;
  line-height: 44px;
}

.link {
  color: #0880ae;
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

  background: url("/check.svg");
  background-repeat: no-repeat;
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
