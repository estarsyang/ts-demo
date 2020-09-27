<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript" target="_blank" rel="noopener">typescript</a></li>
    </ul>
  </div>
</template>

<script lang="ts">
// import Vue from 'vue';
import {Vue, Component} from 'vue-property-decorator'
@Component
export default class HelloWorld extends Vue {
  private msg = 'HelloWorld'
}
// export default Vue.extend({
//   name: 'HelloWorld',
//   props: {
//     msg: String,
//   },
// });
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
