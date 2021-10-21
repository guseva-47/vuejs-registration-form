<template>
  <div class="form-line">
    <label :for="inputId" class="form-label">{{ inputLabel }}</label>
    <input 
      :type="inputType" 
      :id="inputId" 
      :class="input" 
      :name="inputId"
      :placeholder="inputPlaceholder"
      v-model="inputValue"
    />
    <div class="invalid-input">{{ errorMessage }}</div>
  </div>
</template>

<script>
export default {
  name: "FormLine",
  props: {
    inputId: String,
    inputLabel: String,
    inputType: String,
    inputPlaceholder: String
  },
  data() {
    return {
      inputValue: "",
      errorMessage: "Введено некорректное значение",
    };
  },
};
</script>
