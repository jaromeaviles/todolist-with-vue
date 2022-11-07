<template>
  <form @submit.prevent="addTodo()">
    <div class="row">
      <div class="col-12">
        <input ref="inputValue"
          type="text"
          class="form-control"
          placeholder="e.g What to do?"
        />
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

<style scoped>
form {
    margin-top: 50px;
}
input {
    border-radius: 10px;
    margin: 0 auto;
}
</style>