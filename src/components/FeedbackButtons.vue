<template>
  <div>
    <button type="button" @click="incrementLike">
      &#9650; {{ task.likeCounter }}
    </button>
    <button type="button" @click="incrementDislike">
      &#9660; {{ task.dislikeCounter }}
    </button>
  </div>
</template>

<script>
export default {
  props: ["task"],
  methods: {
    incrementLike() {
      this.$emit("incrementLike", this.task);
    },
    incrementDislike() {
      this.$emit("incrementDislike", this.task);
    },
  },
};
</script>
