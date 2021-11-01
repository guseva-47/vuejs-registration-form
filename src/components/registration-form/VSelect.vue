<template>
  <div class="v-select">
    <input
      class="v-select__input"
      :value="!selectedOption ? '' : selectedOption"
      :placeholder="placeholder"
      readonly
      @click="toOpen"
    />
    <ul class="v-select__ul" v-show="open" :style="cssR">
      <li
        class="v-select__li"
        v-for="(option, i) in options"
        :key="i"
        @click="updateOption(option, i)"
        :class="{ 'v-select__li_selected': i == selectedItem }"
      >
        {{ option }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "VSelect",
  props: {
    options: {
      type: [Array, Object],
    },
    selected: {},
    placeholder: String,
    optionsMaxHeight: Number,
  },
  emits: {
    choose: ({ option }) => {
      if (!option) {
        console.warn("Invalid payload for 'choose' event in v-select!");
        return false;
      }
      return true;
    },
  },
  data() {
    return {
      selectedOption: {},
      open: false,
      selectedItem: null,
    };
  },
  created() {
    this.selectedOption = this.selected;
    document.body.addEventListener("click", this.close);
  },
  beforeUnmount() {
    document.body.removeEventListener("click", this.close);
  },
  computed: {
    cssR() {
      const MIN_HEIGHR = 72;
      return { "max-height": `${this.optionsMaxHeight ?? MIN_HEIGHR}px` };
    },
  },
  methods: {
    updateOption(option, i) {
      this.selectedItem = i;
      this.selectedOption = option;
      this.open = false;

      this.$emit("choose", option);
    },
    close(e) {
      if (!this.$el.contains(e.target)) this.open = false;
    },
    toOpen() {
      this.open = true;
    },
  },
};
</script>

<style>
.v-select {
  user-select: none;
  display: inline-block;
  position: relative;
}
.v-select__input {
  display: block;
  width: 100%;
  border: 1px solid #dbe2ea;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 6px;

  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;

  padding: 15px 15px 14px 15px;

  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 21px;

  background: #ffffff url("/chevron-down.svg") 100% no-repeat;
  background-repeat: no-repeat, repeat;
  background-position: right 11px center;
  background-size: 40px;

  cursor: pointer;
}
.v-select__ul {
  list-style: none;
  position: absolute;

  background: #ffffff;
  border: 1px solid #dbe2ea;
  box-sizing: border-box;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04),
    0px 20px 20px rgba(44, 39, 56, 0.04);
  border-radius: 6px;
  padding: 11px 0;

  margin-top: 4px;
  width: 100%;
  min-height: 64px;

  overflow: auto;
  z-index: 20;
}
.v-select__li {
  cursor: pointer;

  font-family: IBM Plex Sans;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 21px;

  padding: 11px 14px 10px 14px;

  color: #756f86;
}
.v-select__li_selected {
  color: #2c2738;
}
.v-select__li:hover {
  background: #ebf4f8;
}
.v-select__input:hover,
.v-select__input:focus {
  border: 2px solid #0880ae;
  padding: 14px 14px 13px 14px;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
}
</style>
