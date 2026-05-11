<script setup>
const props = defineProps({
  status: {
    type: String,
    required: true
  }
});
</script>

<template>
  <div :class="{stop_request_indicator: true, status_none: props.status == 'none', status_stop: props.status == 'stop', status_wheelchair: props.status == 'wheelchair'}">
    <img class="img_stop" src="/assets/img/stop_request.png" alt="STOP">
    <img class="img_wheelchair" src="/assets/img/stop_request_wheelchair.png" alt="STOP-ACC-">
  </div>
</template>

<style scoped>
.stop_request_indicator {
  border: 0.5rem solid white;
  border-radius: 2rem;
  height: max-content;
  position: absolute;
  bottom: 7rem;
  right: 1rem;
}

.stop_request_indicator img {
  width: 6rem;
  margin: 1rem;
}

.stop_request_indicator.status_none {
  opacity: 0.2;
}

.stop_request_indicator.status_none .img_wheelchair {
  display: none;
}

.stop_request_indicator.status_stop {
  opacity: 1;
  background-color: red;
  border-color: transparent;
}

.stop_request_indicator.status_stop .img_wheelchair {
  display: none;
}

.stop_request_indicator.status_wheelchair {
  opacity: 1;
  background-color: hsl(220, 100%, 50%);
  border-color: transparent;
}

.stop_request_indicator.status_wheelchair .img_wheelchair {
  display: block;
}

.stop_request_indicator.status_wheelchair .img_stop {
  display: none;
}
</style>
