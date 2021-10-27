<template>
  <div class="form-line">
    <label :for="inputId" class="form-line__label label">{{
      inputLabel
    }}</label>
    <input
      :type="inputType"
      :id="inputId"
      class="form-line__input input"
      :name="inputId"
      :placeholder="inputPlaceholder"
      v-model="inputValue"
    />
    <div class="error-message" v-if="inputId=='reg-name'" >{{ errorMessage }}</div>
  </div>
</template>

<script>
export default {
  name: "FormLine",
  props: {
    inputId: String,
    inputLabel: String,
    inputType: String,
    inputPlaceholder: String,
  },
  data() {
    return {
      inputValue: "",
      errorMessage: "Введено некорректное значение",
    };
  },
};
</script>

<style>
.form-line {
  display: flex;
  flex-direction: column;
  align-items: stretch;

  min-height: 106px;
}

.form-line__label {
  margin: 0 0 8px 0;
}

.form-line__input {
  margin: 0 0 8px 0;
}

.error-message {
  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 18px;

  color: #ff7171;
}
</style>
