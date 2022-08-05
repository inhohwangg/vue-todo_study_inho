<template>
  <div>
    <ul>
      <li v-for="(a,i) in propsdata" :key="a.item" class="shadow">
        <i class="checkBtn" v-bind:class="{checkBtnCompleted: a.completed}" @click="toggleComplete(a,i)">Check</i>
        <span v-bind:class="{textCompleted: a.completed}">{{a.item}}</span>
        <span class="removeBtn" @click="removeTodo(a,i)">
          <button>버튼</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  //vue 라이프 사이클
  //인스터스가 생성되자마자 호출되는 hook
  methods:{
    removeTodo(a,i) {
      console.log(a, i)
      localStorage.removeItem(a)
      this.todoItems.splice(i, 1)
    },
    /*eslint-disable */
    toggleComplete(a, i) {
      a.completed = !a.completed
      localStorage.removeItem(a.item)
      localStorage.setItem(a.item, JSON.stringify(a))
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>