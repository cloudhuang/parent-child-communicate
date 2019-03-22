<template>
  <div>
    <div>Parent component</div>

    <ul>
      <li>Counter Value: {{ counter }}</li>
      <li>Array Value: {{ arrayValue }}</li>
    </ul>
    
    <div>
      Change Parent Value:
        <ul>
          <li>
            Reset Counter: <button @click="resetCounter">Reset Counter</button>    
          </li>
          <li>

          </li>
        </ul>
    </div>

    <child-component v-model="counter" :counter.sync="counter"></child-component> 
    <child-array-value-component v-model="arrayValue"></child-array-value-component>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent";
import ChildArrayValueComponent from "./ChildArrayValueComponent";

export default {
  name: "HelloWorld",
  components: {
    ChildComponent,
    ChildArrayValueComponent
  },
  data() {
    return {
      counter: 1,
      arrayValue: [1, "2", "Vue.js"],
      msg: "Welcome to Your Vue.js App"
    };
  },
  methods: {
    resetCounter() {
      this.counter = 1;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
