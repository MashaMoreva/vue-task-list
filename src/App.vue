<template>
  <div id="app">
    <h1>Список задач</h1>
    <div v-if="count === 0">Вы великолепны!</div>
    <div v-else-if="count === 1">Остался последний рывок!</div>
    <div v-else>
      Осталось сделать задач: <span class="counter">{{ count }}</span>
    </div>
    <task-list :tasks="uncompletedTasks"></task-list>
    <form @submit.prevent="addTask">
      <div class="form">
        <input :placeholder="placeholderText" v-model="newTask" />
        <button :type="buttonType" :disabled="isButtonDisabled">
          Добавить
        </button>
      </div>
    </form>
    <task-list
      v-if="completedTasks.length"
      :tasks="completedTasks"
      list-title="Завершённые задачи"
    ></task-list>
    <transition name="fade">
      <img
        src="https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663164743_51-mykaleidoscope-ru-p-beshenii-uspekh-krasivo-53.jpg"
        v-show="count === 0"
      />
    </transition>
  </div>
</template>

<script>
import TaskList from "./components/TaskList.vue";

export default {
  components: {
    TaskList,
  },
  data() {
    return {
      newTask: "",
      tasks: [
        {
          text: "Развернуть окружение в Codepen",
          done: true,
          likeCounter: 0,
          dislikeCounter: 0,
        },
        {
          text: "Пройти курс по Vue",
          done: false,
          likeCounter: 0,
          dislikeCounter: 0,
        },
        {
          text: "Сделать интернет-магазин на Vue",
          done: false,
          likeCounter: 0,
          dislikeCounter: 0,
        },
      ],
      placeholderText: "Введите задачу",
      buttonType: "button",
      isButtonDisabled: false,
    };
  },
  methods: {
    addTask() {
      this.tasks.push({ text: this.newTask, done: false });
      this.newTask = "";
    },
  },
  computed: {
    completedTasks() {
      return this.tasks.filter((task) => task.done);
    },
    uncompletedTasks() {
      return this.tasks.filter((task) => !task.done);
    },
    count() {
      return this.uncompletedTasks.length;
    },
  },
};
</script>

<style scoped></style>
