<template>
  <div>
    <button type="button" @click="likeCounter++">
      &#9650; {{ likeCounter }}
    </button>
    <button type="button" @click="dislikeCounter++">
      &#9660; {{ dislikeCounter }}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likeCounter: 0,
      dislikeCounter: 0,
    };
  },
};
</script>
