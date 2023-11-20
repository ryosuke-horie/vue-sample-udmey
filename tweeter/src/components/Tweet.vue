<script setup lang="ts">
const tweets = [{ id: 1, description: "Hello World" }, { id: 2, description: "Hello Vue 3" }];
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
        <input />
        <button class="save-button">post</button>
    </div>
    <div class="tweet-container">
        <ul>
            <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
                <span>{{ tweet.description }}</span>
            </li>
        </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

.tweet-list {
    list-style: none;
}

button {
   color: #fff;
   font-weight: bold;
   background-color: aqua;
   border-radius: 2px;
   border: none;
   width: 60px;
   height: 22px;
}

button:hover {
    background-color: aquamarine;
}

input {
    margin-bottom: 16px;
}
</style>