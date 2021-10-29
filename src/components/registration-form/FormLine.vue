<template>
  <div class="form-line">
    <label :for="params.id" class="form-line__label label">{{
      params.label
    }}</label>
    <input
      :type="params.type"
      :id="params.id"
      class="form-line__input input"
      :name="params.id"
      :placeholder="params.placeholder"
      :value="value"
      @input="$emit('update:value', $event.target.value)"
    />
    <div class="error-message" v-if="!params.isValid">
      {{ errorMessage }}
    </div>
  </div>
</template>

<script>
// import { computed } from "@vue/reactivity";
export default {
  name: "FormLine",
  props: {
    params: {
      type: Object,
      required: true,
      default() {
        return { id: String, label: String, type: String, placeholder: String, isValid: Boolean };
      },
    },
    value: {
      type: String,
      required: true,
    },
  },
  emits: ["update:value"],
  // TODO можно ли использовать??
  // setup: (props, { emit }) => {
  //   const val = computed({
  //     get: () => props.value ?? "",
  //     set: (value) => emit("update:value", value),
  //   });
  //   return { val };
  // },
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
