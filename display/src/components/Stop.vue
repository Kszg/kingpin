<script setup>
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  arrival: {
    type: String,
    required: true
  },
  departure: {
    type: String,
    required: true
  },
  is_last: {
    type: Boolean,
    required: true
  },
  is_active: {
    type: Boolean,
    required: true
  }
});
</script>

<template>
  <div :class="{stop: true, active: props.is_active}">
    <div class="timestamps">
      <p v-if="props.departure" class="departure">{{props.departure}}</p>
      <p v-if="props.arrival" class="arrival">{{props.arrival}}</p>
    </div>
    <div class="marker">
      <div v-if="!props.is_last" class="marker_connector"></div>
    </div>
    <p class="stop_name">{{props.name}}</p>
  </div>
</template>

<style scoped>
.stop {
  width: calc(100% - 2rem);
  border-radius: 2rem;
  display: flex;
  align-items: center;
  padding: 1rem;
  height: 7rem;
}

.stop .timestamps {
  width: max-content;
}

.stop .timestamps > * {
  color: #80818D;
  font-size: 3rem;
  width: 8rem;
  text-align: right;
  line-height: 3rem;
  margin: 0;
}

.stop .marker {
  border-radius: 50%;
  width: 2.5rem;
  aspect-ratio: 1;
  border: 1.5rem solid var(--accent-color);
  margin-inline: 2rem;
  position: relative;
  z-index: 1;
}

.stop .marker_connector {
  border-left: 1.5rem solid var(--accent-color);
  height: 6rem;
  position: absolute;
  left: 50%;
  transform: translateX(-50%) translateY(-6.5rem);
}

.stop .stop_name {
  color: var(--text-main-color);
  font-size: 4rem;
  line-height: 4rem;
  flex: 1;
  margin: 0;
}

.stop.active {
  background-color: var(--text-main-color);
}

.stop.active .stop_name {
  color: var(--bg-color);
}

.stop.active .marker {
  filter: drop-shadow(0 0 0.5rem var(--bg-color));
  background-color: var(--text-main-color);
  z-index: 0;
}
</style>