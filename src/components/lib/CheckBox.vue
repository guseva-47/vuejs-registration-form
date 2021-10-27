<template>
  <input class="checkbox" type="checkbox" />
</template>

<script>
export default {
  name: "CheckBox",
};
</script>

<style>
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

  background-image: url("C:/Users/gusev/Documents/program/hello-work/amigoweb-registration-form/src/assets/Check.png");
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
</style>
