<template>
  <form @submit.prevent="onSubmit">
    <fieldset>
      <legend>Новая задача</legend>
      <input v-model="title" type="text" maxlength="20" placeholder="Деловая" required />
      <input
        v-model="description"
        type="text"
        class="description"
        placeholder="Подготовить договор поставки"
        required
      />
      <button v-show="false" type="submit">Добавить</button>
    </fieldset>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      description: ""
    };
  },
  methods: {
    onSubmit() {
      const newTask = {
        id: Date.now().toString(),
        title: this.title,
        description: this.description,
        stage: "pending",
        editing: false
      };
      this.$emit("add-task", newTask);
      this.title = "";
      this.description = "";
    }
  }
};
</script>

<style scoped>
form {
  width: 500px;
  margin: 10px auto 20px;
}

fieldset,
input {
  border: 2px solid green;
}

input {
  font-size: 1.1rem;
  margin-bottom: 0.7rem;
}

.title {
  width: 260px;
}

.description {
  width: 450px;
}
</style>
