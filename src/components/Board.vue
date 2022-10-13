<template>
  <div class="board">
    <div class="buttons">
      <div class="alphabet">
        <Button
          @showLetter="guessLetter"
          :key="letter.index"
          v-for="letter in alphabet"
          :letter="letter"
        />
      </div>
    </div>
    <br />
    <div class="solution">
      <Button
        :key="solutionLetter.index"
        v-for="solutionLetter in solution"
        :letter="solutionLetter.letter"
        :hide-content="!solutionLetter.guessed"
      />
    </div>
  </div>
</template>

<script>
import Button from "./Button";

export default {
  name: "Board",
  components: {
    Button,
  },

  data() {
    return {
      lives: 10,
      solution: [],
      words: [
        "tree",
        "party",
        "layout",
        "image",
        "seal",
        "berlin",
        "project",
        "structure",
      ],
      alphabet: [..."abcdefghijklmnopqrstuvwxyz"],
    };
  },

  created() {
    this.newGame();
  },
  methods: {
    newGame() {
      this.solution = [];
      const randomWord = this.randomWord();
      for (let i in randomWord) {
        this.solution.push({ letter: randomWord[i], guessed: false });
      }
    },

    guessLetter(letter) {
      let guessedRight = false;
      for (let i in this.solution) {
        const solutionLetter = this.solution[i];
        if (letter === solutionLetter.letter) {
          guessedRight = true;
          solutionLetter.guessed = true;
        }
      }
      if (!guessedRight) {
        this.lives--;
        this.$emit("update:lives", this.lives);
      }
    },

    randomWord() {
      return this.words.sort(() => Math.random() - 0.5)[0];
    },
  },
};
</script>
