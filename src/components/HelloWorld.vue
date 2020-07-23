<template>
  <div>
    <form>
      <button type="button" v-on:click="addTodo">ADD TASK</button>
      <button type="button" v-on:click="removeTodo">
        DELETE FINISHED TASKS
      </button>
      <p>input: <input type="text" v-model="newTodo" /></p>
      <p>task: {{ newTodo }}</p>
    </form>
    <div class="task-list">
      <label class="task-list__item" v-for="todo in todos" :key="todo.id">
        <input type="checkbox" v-model="todo.done" />
        <button>EDIT</button>
        {{ todo.text }}
      </label>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  todos = [
    {
      id: 0,
      text: "vue-router",
      done: false
    },
    {
      id: 1,
      text: "vuex",
      done: false
    },
    {
      id: 2,
      text: "vue-loader",
      done: false
    },
    {
      id: 3,
      text: "awesome-vue",
      done: true
    }
  ];
  newTodo = "";
  addTodo(): void {
    const text = this.newTodo && this.newTodo.trim();
    if (!text) {
      return;
    }
    this.todos.push({
      id: this.getMaxId() + 1,
      text: text,
      done: false
    });
    this.newTodo = "";
  }
  removeTodo(): void {
    for (let i = this.todos.length - 1; i >= 0; i--) {
      if (this.todos[i].done) {
        this.todos.splice(i, 1);
      }
    }
  }
  getMaxId(): number {
    return this.todos.map(t => t.id).reduce((a, b) => Math.max(a, b));
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@mixin flex-vender() {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
}
.task-list {
  @include flex-vender;
  flex-direction: column;
  align-items: center;
  &__item {
    width: 270px;
    text-align: left;
    $element: #{&};
    &--checked {
      @extend #{$element};
      color: #85a6c6;
    }
  }
}
</style>
