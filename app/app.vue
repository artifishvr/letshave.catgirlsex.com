<script setup>
import { ref, onMounted } from 'vue';

const emojis = ref([]);
const emojiCount = 100;

useHead({
  title: "pweaseeeeee",
  link: [
    {
      rel: "icon",
      type: "image/svg+xml",
      href: "/1f97a.svg"
    }
  ],
  meta: [
    {
      name: "description",
      content: "🥺"
    }
  ]
});

onMounted(() => {
  const generatedEmojis = [];
  
  for (let i = 0; i < emojiCount; i++) {
    generatedEmojis.push({
      left: `${Math.random() * 100}vw`,               
      duration: `${Math.random() * 3 + 4}s`,          
      delay: `${Math.random() * 5}s`,                  
      size: `${Math.random() * 2 + 1.5}rem`         
    });
  }
  
  emojis.value = generatedEmojis;

  setInterval(() => {

    if (emojis.value.length >= 1000) {
      return;
    }
const moreEmojis = [];

    for (let i = 0; i < 10; i++) {
    moreEmojis.push({
      left: `${Math.random() * 100}vw`,               
      duration: `${Math.random() * 3 + 4}s`,          
      delay: `${Math.random() * 5}s`,                  
      size: `${Math.random() * 2 + 1.5}rem`         
    });

  }
        emojis.value = emojis.value.concat(moreEmojis);
  }, 1000);

});
</script>

<template>
  <div class="emoji-container">
    <div
      v-for="(emoji, index) in emojis"
      :key="index"
      class="emoji"
      :style="{
        left: emoji.left,
        animationDuration: emoji.duration,
        animationDelay: emoji.delay,
        fontSize: emoji.size
      }"
    >
      <img src="/1f97a.svg" class="size-12" alt="pleading face" />
    </div>
  </div>

  <div class="text-zinc-300/30 absolute bottom-10 right-10 text-right z-10"> 
    <p>by <a href="https://arti.gay" class="text-blue-300/30 underline">arti</a></p>
        <p><a href="https://github.com/jdecked/twemoji" class="text-blue-300/30 underline">twemoji</a> under CC-BY 4.0</p>
  </div>
</template>

<style>
body {
  @apply bg-zinc-950
}

.emoji-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  overflow: hidden;
  z-index: 0; 
}

.emoji {
  position: absolute;
  top: -100px; 
  animation: fall linear infinite;
  user-select: none;
}

@keyframes fall {
  0% {
    transform: translateY(0) rotate(-15deg);
    opacity: 1;
  }
  100% {
    transform: translateY(120vh) rotate(15deg);
    opacity: 0.2;
  }
}
</style>