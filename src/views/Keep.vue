<template>
  <div>
  <button
    v-for="tab in tabs"
    v-bind:key="tab"
    v-bind:class="['tab-button', { active: currentTab === tab }]"
    v-on:click="currentTab = tab"
  >
    {{ tab }}
  </button>
  <keep-alive>
    <component :is="currentTabComponent" class="tab"></component>
  </keep-alive>
</div>
</template>

<script>

import KeepAliveFormTab from '@/components/KeepAlive/FormTab'
import KeepAliveTextTab from '@/components/KeepAlive/TextTab'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Keep',
  components: { KeepAliveTextTab, KeepAliveFormTab },
  data () {
    return {
      currentTab: 'Form',
      tabs: ['Form', 'Text']
    }
  },
  computed: {
    currentTabComponent () {
      return 'KeepAlive' + this.currentTab + 'Tab'
    }
  }
}
</script>

<style scoped>

</style>
