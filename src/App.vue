<template>
  <div id="app">
    <CampaignForm></CampaignForm>
  </div>
</template>

<script>
import CampaignForm from './components/CampaignForm.vue';

export default {
  name: 'app',
  components: {
    CampaignForm,
  },
};
</script>

<style lang="scss">
@import './styles/reset.scss';
#app {
  font-family: 'PT Sans';
  font-size: 16px;
  font-family: Roboto, Arial, sans-serif;
}
</style>
