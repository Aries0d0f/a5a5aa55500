<template>
  <template v-for="color in colorBlocks" :key="color">
    <Color :color="color"/>
  </template>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import _ from 'lodash';

import Color from './components/Color.vue'

export default defineComponent({
  name: 'App',
  components: {
    Color
  },
  setup(props) {
    const lyrics = 'A5A5AA555OOEAEAA555OOEAA5OOOA5A5AA555OOEAEAA555OOEAA5OOO';

    const lyrics2Hex = (raw: string): string => raw.replace(/O/gm, '0');

    const hexColorParser = (raw: string): string[] => {
      return _(raw).chunk(6).filter(['length', 6]).map((chunk: string[]) => `#${_.join(chunk, '')}`);
    }

    return {
      colorBlocks: hexColorParser(lyrics2Hex(lyrics))
    }
  },
})
</script>

<style lang="scss">
@import "style/scss/main.scss";
</style>
