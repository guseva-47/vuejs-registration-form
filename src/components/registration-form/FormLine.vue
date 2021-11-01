<template>
  <div class="form-line">
    <label :for="params.id" class="form-line__line label">
      {{ params.label }}
    </label>

    <input
      :type="params.type"
      :id="params.id"
      class="form-line__line input"
      :name="params.id"
      :placeholder="params.placeholder"
      v-model="val"
      @blur="onBlur"
    />

    <div class="form-line__error-message" v-if="!params.isValid">
      {{ errorMessage }}
    </div>
  </div>
</template>

<script>
import { computed } from "@vue/reactivity";
export default {
  name: "FormLine",
  props: {
    value: { type: String, required: true },
    errorMessageText: String,
    params: {
      type: Object,
      required: true,
      default() {
        return {
          id: String,
          label: String,
          type: String,
          placeholder: String,
          isValid: Boolean,
        };
      },
    },
  },
  emits: {
    "update:value": null,
    forBlur: null,
  },
  setup: (props, { emit }) => {
    const val = computed({
      get: () => props.value ?? "",
      set: (value) => emit("update:value", value),
    });

    const onBlur = () => {
      emit("forBlur", props.value);
    };

    const errorMessage = props.errorMessageText ?? "Введено некорректное значение";

    return { val, errorMessage, onBlur };
  },
};
</script>

<style scoped>
.form-line {
  display: flex;
  flex-direction: column;
  align-items: stretch;

  min-height: 106px;
}

.form-line__line {
  margin: 0 0 8px 0;
}

.form-line__error-message {
  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 18px;

  color: #ff7171;
}
</style>
