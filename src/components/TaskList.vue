<template>
  <div id="app">
    <h1>Список задач</h1>
    <div v-if="count() == 0">Вы великолепны!</div>
    <div v-else-if="count() == 1">Остался последний рывок!</div>
    <div v-else>
      Осталось сделать задач: <span class="counter">{{ count() }}</span>
    </div>
    <div class="list">
      <div class="item" :class="{ done: task.done }" v-for="task in tasks">
        <input type="checkbox" v-model="task.done" />
        {{ task.text }}
      </div>
    </div>
    <form class="form" @submit.prevent="addTask">
      <input :placeholder="placeholderText" v-model="newTask" />
      <button :type="buttonType" :disabled="isButtonDisabled" @click="addTask">
        Добавить
      </button>
    </form>
    <transition name="fade">
      <img
        src="https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663164743_51-mykaleidoscope-ru-p-beshenii-uspekh-krasivo-53.jpg"
        v-show="count() == 0"
      />
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [
        { text: "Развернуть окружение в Codepen", done: true },
        { text: "Пройти курс по Vue", done: false },
        { text: "Сделать интернет-магазин на Vue", done: false },
      ],
      placeholderText: "Введите задачу",
      buttonType: "submit",
      isButtonDisabled: false,
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push({ text: this.newTask, done: false });
        this.newTask = "";
      }
    },
    count() {
      return this.tasks.filter((task) => !task.done).length;
    },
  },
};
</script>

<style scoped></style>
