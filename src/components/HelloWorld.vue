<template>
  <div class="hello">
    <p>data:{{ msg }}</p>
    <p>props:{{ propsValue }}</p>
    <p>computed: {{computedValue}}</p>
    <p>watch {{watchValue}}</p>
    <input
      type="text"
      v-model="msg"
    />
    <RefDemo ref="refdemo" />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from "vue-property-decorator";
import RefDemo from "./RefDemo.vue";
@Component({
  name: "helloworld",
  components: {
    RefDemo,
  },
})
export default class HelloWorld extends Vue {
  // props
  @Prop({ default: "props defaultValue", type: String, required: false })
  readonly propsValue!: string;
  // computed
  get computedValue():string {
    return "computed defaultValue";
  }
  // watch
  @Watch("msg")
  onMsgChange(val: string, oldVal: string):void {
    console.log(val);
    console.log(oldVal);
    
    this.changeWatchValue(val);
  }
  // data
  private msg = "HelloWorld";
  private watchValue = "";
  // methods
  changeWatchValue(val: string):void {
    this.watchValue = val;
  }
  // lifecycle
  mounted():void {
    console.log(this.$refs.refdemo);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
