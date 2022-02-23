<script setup lang="ts">
const emits = defineEmits(['focus', 'blur'])
const word: string = $ref('')

const challengeLink = $computed(() => {
  return `https://joguinho-dusgu.netlify.app/?${btoa(word.toLowerCase())}`
})

const copyChallenge = () => {
  navigator.clipboard.writeText(challengeLink)
}
</script>

<template>
  <div id="challenge">
    <h2>Criar desafio</h2>
    <div class="challenge-container">
      <input
        ref="input"
        type="text"
        v-model="word"
        placeholder="Palavra para desafiar"
        @focus="$emit('focus')"
        @blur="$emit('blur')"
      />
      <button @click="copyChallenge">Copiar link do desafio</button>
    </div>
  </div>
</template>

<style scoped>
#challenge {
  margin-top: 3.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.challenge-container {
  width: 360px;
  display: flex;
}

h2 {
  color: #fff;
}

input {
  border: 0;
  flex: 1;
  padding: 0.5rem 1rem;
  font-size: 1rem;
}

input:focus {
  outline: 0;
}

button {
  border: 0;
  background-color: #3e9197;
  color: #fff;
  font-weight: bold;
  padding: 0.5rem 0.8rem;
  text-transform: uppercase;
  line-height: 1.4;
  transition: all 0.333s;
}

button:hover {
  background-color: #2e787e;
  cursor: pointer;
}

button:focus {
  background-color: #2e7e39;
  cursor: pointer;
}
</style>
