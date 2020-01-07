<template>
  <form class="form" action>
    <h3>Where would you like to display your campaign?</h3>
    <CampaignFormItem
      v-for="(rule, index) in rules"
      :key="index"
      :ruleIndex="index"
      :format="rule.format"
      :url="rule.url"
      :removeRule="removeRule"
      @fieldChange="handleValueChange"
    ></CampaignFormItem>
    <Button :onClick="addRule">+ New rule</Button>
    <ReactiveTable v-if="rules.length > 0" :rules="rules"></ReactiveTable>
  </form>
</template>

<script>
import Button from './UIKit/Button.vue';
import CampaignFormItem from './CampaignFormItem.vue';
import ReactiveTable from './ReactiveTable.vue';

export default {
  name: 'CampaignForm',
  components: {
    Button,
    CampaignFormItem,
    ReactiveTable,
  },
  data: () => ({
    rules: [],
  }),
  methods: {
    addRule() {
      this.rules = [
        ...this.rules,
        {
          format: 'contains',
          url: '',
        },
      ];
    },
    removeRule(index) {
      this.rules = [
        ...this.rules.slice(0, index),
        ...this.rules.slice(index + 1),
      ];
    },
    handleValueChange(newValue, ruleIndex, fieldName) {
      const changedRule = this.rules[ruleIndex];

      this.rules = [
        ...this.rules.slice(0, ruleIndex),
        {
          ...changedRule,
          [fieldName]: newValue,
        },
        ...this.rules.slice(ruleIndex + 1),
      ];
    },
  },
};
</script>

<style scoped lang="scss">
.form {
  max-width: 1200px;
  margin: 50px auto;
  padding: 0 20px;
}
</style>
