<template>
  <div class="color color-container">
    <div class="color color-block" :style="{ '--color': color }"></div>
    <aside class="color color-mark"><p>{{ color }}</p></aside>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
export default defineComponent({
  name: 'Color',
  props: {
    color: {
      type: String,
      required: true
    }
  },
  setup: (props) => {
    const color = ref(props.color);
    return { color };
  }
})
</script>

<style lang="scss" scoped>
.color {
  &-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 4px;
  }

  &-block {
    background-color: var(--color);
    height: 48px;
    width: 48px;
  }

  &-mark {
    padding-left: 8px;
  }
}
</style>