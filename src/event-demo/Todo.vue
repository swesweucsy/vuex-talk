<template>
  <div id="todo">
    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.message }}
      </li>
    </ul>
    <div>
      <input type="text" v-model="input"/>
      <button v-on:click="submit">Submit</button>
    </div>
  </div>
</template>

<script>
import EventBus from './event-bus'

export default {
    name: "Todo",
    data: function() {
      return {
        input: '',
        items: []
      };
    },
    methods: {
      submit: function ()  {
        EventBus.$emit('todo-add', { message: this.input });
        this.items.push({ message: this.input })
        this.input = ""
      }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#todo{
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

ul {
  list-style-type: none;
  padding: 0;
  width: 500px;
}

li {
  border-bottom: 1px solid rgb(230, 230, 230);
  padding: 15px;
}

input{
  height: 40px;
  width: 300px;
}

button{
  height: 45px;
  font-size: 14px;
  background: blue;
  border:0;
  color: white;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
</style>
