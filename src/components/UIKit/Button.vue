<template>
  <button @click="onClick" type="button" class="button">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    onClick: Function,
  },
};
</script>

<style lang="scss" scoped>
.button {
  outline: none;
  font-weight: 500;
  font-size: 1rem;
  border: 2px solid #dadfe6;
  border-radius: 0.375rem;
  color: #2a2a2a;
  background-color: transparent;
  padding: 0.75rem 1.5rem;
  text-transform: uppercase;
  letter-spacing: 0.4px;
  cursor: pointer;

  transition: background-color 0.2s, color 0.2s, border-color 0.2s;

  &:hover {
    background-color: #dadfe6;
  }

  &:active {
    border-color: #bbc0c6;
    background-color: #bbc0c6;
    color: #2a2a2a;
  }
}
</style>
