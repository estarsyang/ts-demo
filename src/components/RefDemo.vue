<template>
  <div>
    {{msg}}
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
@Component
export default class Index extends Vue {
  private msg ='这是一个refs使用demo'
}
</script>

<style scoped lang="less">
</style>
