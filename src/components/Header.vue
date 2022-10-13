<template>
  <div class="header">
    <h1>{{ game }}</h1>
    <h2>Welcome to my {{ game }} Game</h2>
    <p>
      Use the alphabet below to guess the word. You have {{ lives }} lives so
      try your best.
    </p>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    lives: Number,
  },
  data() {
    return {
      game: "Hangman",
    };
  },
};
</script>
