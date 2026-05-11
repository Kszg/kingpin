<script setup>
import FooterLineList from './FooterLineList.vue';

import { ref, useTemplateRef, onMounted, onUnmounted } from 'vue';

const connections = [
  {
    iconPath: "/img/flixbus.png",
    accentColor: "#73D700",
    accentFgColor: "#272524",
    lines: [
      "N101",
      "N202"
    ]
  },
  {
    iconPath: "/img/cbus.png",
    accentColor: "#149EDA",
    accentFgColor: "#FFFFFF",
    lines: [
      "5",
      "7",
      "67",
      "234E"
    ]
  },
  {
    iconPath: "/img/trolley.png",
    accentColor: "#E4191F",
    accentFgColor: "#FFFFFF",
    lines: [
      "83"
    ]
  },
  {
    iconPath: "/img/tram.png",
    accentColor: "#FFDA00",
    accentFgColor: "#272424",
    lines: [
      "4",
      "6"
    ]
  },
  {
    iconPath: "/img/metro3.png",
  },
  {
    iconPath: "/img/ic.png",
  }
]

const connectionsOverflowing = ref(false);
const connectionsRef = useTemplateRef("connections");

function onClientResized() {
  connectionsOverflowing.value = connectionsRef.value.scrollWidth > connectionsRef.value.clientWidth;
  console.log(`${connectionsRef.value.scrollWidth} > ${connectionsRef.value.clientWidth}: ${connectionsRef.value.scrollWidth > connectionsRef.value.clientWidth} = ${connectionsOverflowing.value}`)
}

onMounted(() => {
  window.addEventListener('resize', onClientResized);
  setTimeout(onClientResized, 0);
  autoscroll();
});

onUnmounted(() => {
  window.removeEventListener('resize', onClientResized);
});

const scrollSpeed = 0;
let animationId;

function autoscroll() {
  const em = connectionsRef.value;

  em.scrollLeft += scrollSpeed;

  if (em.scrollLeft >= em.scrollWidth / 2) {
    em.scrollLeft = 0;
  }

  animationId = requestAnimationFrame(autoscroll);
}
</script>

<template>
  <div class="footer">
    <div class="connections" ref="connections">
      <FooterLineList :lines="connections"/>
      <p class="connection_loop_separator">***</p>
      <FooterLineList :lines="connections" v-if="connectionsOverflowing"/>
    </div>
    <img class="logo" src="/img/logo.png" alt="LOGO">
  </div>
</template>

<style scoped>
.footer {
  width: calc(100% - 1rem);
  padding-right: 1rem;
  height: 6rem;
  background-color: var(--header-color);
  display: flex;
  align-items: center;
  gap: 1rem;
  padding-left: 0;
}

.footer .connections {
  scrollbar-width: none;
  height: 100%;
  overflow-x: auto;
  overflow-y: visible;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.footer .connection_loop_separator {
  font-size: 4.5rem;
  color: var(--text-main-color);
  margin-left: 12rem;
  margin-right: 7rem;
  margin-block: 0;
}

.footer .logo {
  height: 5rem;
}
</style>
