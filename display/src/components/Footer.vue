<script setup>
import LineList from './LineList.vue';

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
</script>

<template>
  <div class="footer">
    <div class="connections">
      <LineList :lines="connections"/>
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

.footer .logo {
  height: 5rem;
}
</style>
