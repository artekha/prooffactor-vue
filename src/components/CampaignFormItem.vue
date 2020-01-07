<template>
  <section class="wrapper">
    <p>
      Type a full or partial url where you would like to display notifications.
    </p>
    <div class="close" @click="removeRule(ruleIndex)"></div>
    <div class="fields">
      <SelectField
        class="fields__select"
        :value="format"
        @change="onFieldChange(...arguments, ruleIndex, 'format')"
        :options="selectOptions"
      ></SelectField>
      <TextField
        :value="url"
        @change="onFieldChange(...arguments, ruleIndex, 'url')"
        class="fields__input"
        placeholder="Display URL"
      ></TextField>
    </div>
  </section>
</template>

<script>
import TextField from './UIKit/TextField.vue';
import SelectField from './UIKit/SelectField.vue';

const SELECT_OPTIONS = [
  {
    value: 'contains',
    title: 'Contains',
  },
  {
    value: 'exact_match',
    title: 'Exact Match',
  },
];

export default {
  name: 'CampaignFormItem',
  components: {
    TextField,
    SelectField,
  },
  props: {
    removeRule: Function,
    ruleIndex: Number,
    format: String,
    url: String,
  },
  data: () => ({
    selectOptions: SELECT_OPTIONS,
  }),
  methods: {
    onFieldChange(newValue, ruleIndex, fieldName) {
      this.$emit('fieldChange', newValue, ruleIndex, fieldName);
    },
  },
};
</script>

<style scoped lang="scss">
.wrapper {
  position: relative;
  border: 1px solid #dadfe6;
  border-radius: 6px;
  padding: 30px;
  margin-bottom: 40px;
  box-shadow: 0px 8px 10px -5px #f7f8fa;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 32px;
  height: 32px;
  background-image: url('../assets/close.png');
  background-size: 100%;
  cursor: pointer;
  opacity: 0.3;
  transition: opacity 0.2s;

  &:hover {
    opacity: 1;
  }
}

.fields {
  display: flex;
  &__select {
    min-width: 300px;
    margin-right: 30px;
  }
  &__input {
    flex: 1 1 100%;
  }
}
</style>
