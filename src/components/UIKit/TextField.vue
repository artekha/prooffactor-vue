<template>
  <div :class="{ error: error }">
    <input
      @input="
        updateValue($event);
        validate($event);
      "
      @blur="validate"
      :value="value"
      :placeholder="placeholder"
      class="input"
      type="text"
    />
    <div v-if="error" class="error__message">{{ error }}</div>
  </div>
</template>

<script>
export default {
  name: 'TextField',
  props: {
    placeholder: String,
    value: String,
  },
  data: () => ({
    error: null,
  }),
  methods: {
    updateValue(e) {
      this.$emit('change', e.target.value);
    },
    validate(e) {
      const { value } = e.target;

      if (!value || (value && value.trim().length < 1)) {
        this.error = 'URL is Missing';
      } else {
        this.error = null;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@keyframes errorAppearance {
  0% {
    transform: translateX(-5px);
  }
  25% {
    transform: translateX(5px);
  }
  50% {
    transform: translateX(-5px);
  }
  100% {
    transform: translateX(0px);
  }
}

.input {
  outline: none;
  font-size: 1rem;
  border: 2px solid #dadfe6;
  border-radius: 6px;
  color: #2a2a2a;
  background-color: transparent;
  padding: 12px 20px;
  width: 100%;

  &::placeholder {
    color: #aaafb5;
    transition: color 0.2s;
  }

  &:focus::placeholder {
    color: transparent;
  }
}
.error {
  .input {
    border-color: #fd506d;
  }
  &__message {
    padding: 12px 20px;
    color: #fd506d;
    background-color: #f5f7f8;
    border-radius: 6px;
    animation-name: errorAppearance;
    animation-duration: 0.2s;
  }
}
</style>
