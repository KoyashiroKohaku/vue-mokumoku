<template>
  <div>
    {{ msg }}
    <form>
      <button>ADD TASK</button>
      <button>DELETE FINISHED TASKS</button>
      <p>input: <input type="text" /></p>
      <p>task:</p>
    </form>
    <div class="task-list">
      <label class="task-list__item">
        <input type="checkbox" /><button>EDIT</button>vue-router
      </label>
      <label class="task-list__item">
        <input type="checkbox" /><button>EDIT</button>vuex
      </label>
      <label class="task-list__item">
        <input type="checkbox" /><button>EDIT</button>vue-loader
      </label>
      <label class="task-list__item--checked">
        <input type="checkbox" /><button>EDIT</button>awesome-vue
      </label>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
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
