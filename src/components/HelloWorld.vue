<template>
  <div>
    <p>count:{{count}}</p>
    <div v-bind:title="time" v-on:click="handleOnClick">{{msg}}</div>
    <p>{{time}}</p>
    <p>input: {{input}}</p>
    <p>computed: {{reverseInput}}</p>
    <p>methods: {{reverseInputMethod()}}</p>
    <input v-model="input">
    <div>------</div>
    <todo-item
        v-for='item in groceryList'
        v-bind:todo="item"
        v-bind:key="item.id"
    ></todo-item>
    <p>未使用v-html:{{rawHtml}}</p>
    <p>使用了v-html:<span v-html="rawHtml"></span></p>
    <p v-html="rawHtml">使用了v-html:</p>
    <div>time-item</div>
    <time-item ref="timeItem"></time-item>
  </div>
</template>

<script>
  import TodoItem from "./todo-item";
  import TimeItem from "./time-item";

  export default {
    name: 'HelloWorld',
    components: {
      TodoItem,
      TimeItem
    },
    props: {
      msg: String
    },
    data() {
      return {
        constant: 'abc',
        count: 0,
        time: '页面加载于' + new Date().toLocaleString(),
        input: '',
        groceryList: [
          {id: 0, text: '蔬菜'},
          {id: 1, text: '奶酪'},
          {id: 2, text: '随便其它什么人吃的东西'}
        ],
        rawHtml: '<span style = "color: red">This should be red</span>'
      }
    },
    mounted() {
      setInterval(this.counting, 1000);
    },
    methods: {
      counting: function () {
        this.count = this.count + 1;

      },
      handleOnClick: function () {
        alert('click');
      },
      reverseInputMethod: function () {
        console.log('reverse');
        this.time = new Date().toString();
        return this.input.split('').reverse().join('') + new Date().toString()
      }
    },
    computed: {
      reverseInput: function () {
        return this.input.split('').reverse().join('') + new Date().toString() + this.constant
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
