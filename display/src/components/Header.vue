<script setup></script>

<template>
  <div class="header">
    <img class="route_logo" src="/img/flixbus.png">
    <p class="line_number">N101</p>
    <svg class="line_arrow" xmlns="http://www.w3.org/2000/svg" viewBox="256 160 192 320"><!-- !Font Awesome Free v7.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2026 Fonticons, Inc. --><path d="M441.3 299.8C451.5 312.4 450.8 330.9 439.1 342.6L311.1 470.6C301.9 479.8 288.2 482.5 276.2 477.5C264.2 472.5 256.5 460.9 256.5 448L256.5 192C256.5 179.1 264.3 167.4 276.3 162.4C288.3 157.4 302 160.2 311.2 169.3L439.2 297.3L441.4 299.7z"/></svg>
    <p class="destination">Budapest, Népliget autóbusz-pályaudvar</p>
    <p class="clock">13:25</p>
  </div>
</template>

<style scoped>
.header {
  width: calc(100vw - 2rem);
  height: 7rem;
  background-color: var(--header-color);
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
}

.route_logo {
  height: 100%;
}

.line_number {
  background-color: var(--accent-color);
  color: var(--accent-fg-color);
  border-radius: 1.5rem;
  font-size: 4rem;
  padding: 0.75rem;
}

.line_arrow {
  fill: var(--text-main-color);
  height: 50%;
}

.destination {
  color: var(--text-main-color);
  font-size: 4rem;
  line-height: 4rem;
  flex: 1;
}

.clock {
  color: var(--text-main-color);
  opacity: 50%;
  font-size: 4rem;
  text-align: center;
}
</style>
