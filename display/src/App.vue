<script setup>
import Header from '@/components/Header.vue';
import Footer from './components/Footer.vue';
import Stop from './components/Stop.vue';
import StopRequestIndicator from './components/StopRequestIndicator.vue';
</script>

<template>
  <div class="display">
    <Header/>
    <div class="stop_area">
      <div class="stops">
        <div class="upcoming_stops">
          <Stop name="Taksony, községháza" arrival="14:45" :is_last="true"/>
          <Stop name="Dunavarsány, vasútálomás" arrival="14:05" :is_last="false"/>
          <Stop name="Délegyháza, II. tó" arrival="13:50" :is_last="false"/>
          <Stop name="Délegyháza, vasútálomás dkjfjhgdsjkgjsdfkg sdfg " arrival="13:42" departure="13:45" :is_last="false"/>
        </div>
        <Stop name="Délegyháza, vasútálomás dkjfjhgdsjkgjsdfkg sdfg " arrival="13:42" departure="13:45" :is_last="false" :is_active="true"/>
      </div>
      <StopRequestIndicator status="none"/>
    </div>
    <Footer/>
  </div>
</template>

<style scoped>
.display {
  width: 100vw;
  height: 100vh;
  background-color: var(--bg-color);
  display: flex;
  flex-direction: column;
}

.stop_area {
  flex: 1;
  display: flex;
}
</style>
