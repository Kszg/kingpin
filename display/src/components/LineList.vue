<script setup>
const props = defineProps({
  lines: {
    type: Object,
    required: true
  }
});

function getElements() {
  let ret = [];
  
  // console.log("props.lines", props.lines);

  props.lines.forEach(category => {
    ret.push({
      type: "icon",
      iconPath: category.iconPath
    });
    
    console.log("category.lines", category.lines);

    if (category.lines) {
      category.lines.forEach(line => {
        ret.push({
          type: "label",
          text: line,
          bg: category.accentColor,
          fg: category.accentFgColor
        });
      });
    }
  });
  
  return ret;
}

const elements = getElements();

</script>

<template>
  <div :class="{container: true, label_container: e.type == 'label'}" v-for="(e, i) in elements" :key="i" :style="e.type == 'label' ? `background-color: ${e.bg}; color: ${e.fg};` : ''">
    <img class="icon" v-if="e.type == 'icon'" :src="e.iconPath" alt="Service icon">
    <p class="label" v-if="e.type == 'label'">{{ e.text }}</p>
  </div>
</template>

<style scoped>
.container .icon {
  height: 5rem;
  margin-left: 5rem;
}

.container:first-child .icon {
  margin-left: 1rem;
}

.label_container {
  border-radius: 1rem;
  margin: 0;
  margin-left: 1rem;
  padding: 0.5rem 1rem;
}

.container .label {
  font-size: 3rem;
  margin: 0;
}
</style>