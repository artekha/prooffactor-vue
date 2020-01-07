<template>
  <div>
    <h3>Check reactivity</h3>
    <table class="table">
      <tr class="table__row">
        <th class="table__column table__column_header">Format</th>
        <th class="table__column table__column_header">URL</th>
      </tr>
      <tr class="table__row" v-for="(rule, index) in rules" :key="index">
        <td class="table__column">{{ rule.format }}</td>
        <td class="table__column">{{ rule.url || '–' }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ReactiveTable',
  props: {
    rules: Array,
  },
};
</script>

<style scoped lang="scss">
.table {
  width: 100%;
  padding: 0;
  margin: 0;
  &__row {
    border-bottom: 1px solid #dadfe6;
    &:last-child {
      border-bottom: none;
    }
  }
  &__column {
    width: 50%;
    padding: 20px;
    border-right: 1px solid #dadfe6;
    &_header {
      font-weight: 600;
    }
    &:last-child {
      border-right: none;
    }
  }
}
</style>
