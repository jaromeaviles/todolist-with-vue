<template>
  <form @submit.prevent="addTodo()">
    <div class="row align-items-center justify-content-center">
      <div class="col-auto">
        <input ref="inputValue"
          type="text"
         
          class="form-control"
          placeholder="e.g What to do?"
        />
      </div>
      <div class="col-auto">
        <button class="btn btn-success">Submit</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
    emits: ['added-todo'],
    methods: {
        addTodo() {
            if (this.$refs.inputValue.value == '') {
                return;
            }
            let todo = {
                id: Math.floor(Math.random() * 1000),
                todoName: this.$refs.inputValue.value
            }
            this.$emit('added-todo', todo);
            this.$refs.inputValue.value = '';
        }
    }
};
</script>