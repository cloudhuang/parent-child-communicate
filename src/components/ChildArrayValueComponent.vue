<template>
  <div id="child">
    <span>This is the child component 2:</span>

    <div>
        Value from parent: {{ inputListValue }}
    </div>

    <div>
        <ul>
            <li>Reverse Array: <button @click="reverseArray">Reverse Array</button></li>
            <li>Add New Element: 
        <input type="text" v-model="elementValue"><button @click="addNewElement">Add New Element</button></li>
        </ul>
    </div>

    <div>
        演示Array类型的属性，父组件与子组件的通信<br/>
        1. 点击"Reverse Array"按钮，子组件的值传递回父组件，即修改父组件中的'v-model'的模型数据<br/>
        2. 点击"Add New Element"按钮，新增值到数据中，并传递回父组件
    </div>
  </div>
</template>

<script>
/**
 * 传递数组
 */
export default {
  name: "ChildArrayValueComponent",
  props: {
    value: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return {
        inputListValue: this.value,
        elementValue: null,
    };
  },

  watch: {
      inputListValue(val) {
          this.$emit("input", val);
      }
  },
  methods: {
      reverseArray() {
          this.inputListValue.reverse();
      },

      addNewElement() {
          if (this.elementValue) {
                this.inputListValue.push(this.elementValue);
          }
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
