<script setup>
import FooterLineList from './FooterLineList.vue';
import { ref, onMounted, onUnmounted } from 'vue';

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

const connectionsRef = ref();
const lineListRef = ref();
const connectionLoopSeparatorRef = ref();

const connectionsOverflowing = ref(false);

function onClientResized() {
  connectionsOverflowing.value = lineListRef.value.$el.clientWidth > connectionsRef.value.clientWidth;
  
  if (connectionsOverflowing.value) startScrollAnim();
  else stopScrollAnim();
}

onMounted(() => {
  window.addEventListener('resize', onClientResized);
  setTimeout(onClientResized, 0);
});

onUnmounted(() => {
  window.removeEventListener('resize', onClientResized);
});

const scrollSpeed = 3;
let scrollAnimationId = null;

function startScrollAnim() {
  if (scrollAnimationId != null) return;
  scrollAnimFrame();
}

function stopScrollAnim() {
  cancelAnimationFrame(scrollAnimationId);
  scrollAnimationId = null;
}

function scrollAnimFrame() {
  const em = connectionsRef.value;
  const listEm = lineListRef.value.$el;
  const sepEm = connectionLoopSeparatorRef.value;

  em.scrollLeft += scrollSpeed;

  if (em.scrollLeft >= (listEm.clientWidth + sepEm.clientWidth)) {
    em.scrollLeft = 0;
  }

  scrollAnimationId = requestAnimationFrame(scrollAnimFrame);
}
</script>

<template>
  <div class="footer">
    <div class="connections" ref="connectionsRef">
      <FooterLineList :lines="connections" ref="lineListRef"/>
      <p class="connection_loop_separator" ref="connectionLoopSeparatorRef" v-show="connectionsOverflowing">***</p>
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
  padding: 0 10rem;
}

.footer .logo {
  height: 5rem;
}
</style>
