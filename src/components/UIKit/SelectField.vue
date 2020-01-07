<template>
  <div>
    <select @change="updateValue" class="select">
      <option
        v-for="option in options"
        :value="option.value"
        :key="option.value"
      >
        {{ option.title }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'SelectField',
  props: {
    options: Array,
  },
  methods: {
    updateValue(e) {
      this.$emit('change', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  outline: none;
  font-size: 1rem;
  border: 2px solid #dadfe6;
  border-radius: 6px;
  color: #2a2a2a;
  background-color: transparent;
  padding: 12px 20px;
  width: 100%;
  height: 46px;
}
</style>
