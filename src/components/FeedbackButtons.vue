<template>
  <div>
    <button type="button" @click="incrementLike">
      &#9650; {{ likeCounter }}
    </button>
    <button type="button" @click="incrementDislike">
      &#9660; {{ dislikeCounter }}
    </button>
  </div>
</template>

<script>
export default {
  props: ["task", "likeCounter", "dislikeCounter"],
  methods: {
    incrementLike() {
      this.$emit("update:likeCounter", this.likeCounter + 1);
    },
    incrementDislike() {
      this.$emit("update:dislikeCounter", this.dislikeCounter + 1);
    },
  },
};
</script>
