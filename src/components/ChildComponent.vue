<template>
  <div id="child">
    <span>This is the child component 1:</span>
    <div>Value from parent component: {{ inputValue }}</div>
    <ul>
      <li>
        <button @click="increaseCounter">Increase Counter</button>
      </li>
    </ul>

    <div>
        演示Number类型的属性，父组件与子组件的通信<br/>
        1. 点击Increase Counter按钮，子组件的值传递回父组件，即修改父组件中的'v-model'的模型数据<br/>
        2. 点击父组件的"Reset Counter"按钮重置按钮，父组件重置Counter属性，同时将新的值同步至子组件<br/>
        
        如果需要父子组件双向传递，则需要同时配置'v-model'和子组件的'props'
    </div>
  </div>
</template>

<script>
/**
 * 传递单个数字
 */
export default {
  name: "ChildComponent",
  props: {
    value: {
      type: Number,
      default() {
        return 0;
      }
    },
    counter: {
      type: Number,
      default() {
        return 0;
      }
    }
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      inputValue: this.counter
    };
  },

  watch: {
    inputValue(newVal, oldVal) {
      this.$emit("input", newVal);
    },
    counter(newVal, oldVal) {
        this.inputValue = newVal;
    }
  },
  methods: {
    increaseCounter() {
      this.inputValue++;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#child {
  border: 1px solid red;
  padding: 10px;
  margin: 10px;
}

ul li {
  margin: 5px;
}
</style>
