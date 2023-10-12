<template>
  <div class="list" v-if="tasks.length > 0">
    <h2>{{ listTitle }}</h2>
    <div
      class="item"
      :class="{ done: task.done }"
      v-for="task in tasks"
      :key="task.text"
    >
      <input type="checkbox" v-model="task.done" />
      {{ task.text }}
      <feedback-buttons
        :task="task"
        @incrementLike="incrementLike"
        @incrementDislike="incrementDislike"
      ></feedback-buttons>
    </div>
  </div>
</template>

<script>
import FeedbackButtons from "./FeedbackButtons.vue";

export default {
  components: {
    FeedbackButtons,
  },
  props: ["tasks", "listTitle"],
  methods: {
    incrementLike(task) {
      task.likeCounter++;
    },
    incrementDislike(task) {
      task.dislikeCounter++;
    },
  },
};
</script>
