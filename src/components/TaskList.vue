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
      <feedback-buttons></feedback-buttons>
    </div>
  </div>
</template>

<script>
export default {
  props: ["tasks", "listTitle"],
};
</script>
