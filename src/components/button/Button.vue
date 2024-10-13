<!-- eslint-disable vue/multi-word-component-names -->
<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'

export default defineComponent({
  props: {
    title: {
      type: String as PropType<string>,
      requered: true
    },
    id: {
      type: Number as PropType<number>,
      required: true
    },
    clickHandler: {
      type: Function as PropType<(id: number) => void>,
      required: true
    }
  },
  setup(props) {
    return {
      props
    }
  }
})
</script>

<template>
  <button class="btn btn--base" @click="clickHandler(id)">{{ props.title }}</button>
</template>

<style scoped>
.btn {
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.btn--base {
  padding: 15px 40px;
  background:
    linear-gradient(40deg, rgb(61, 105, 155) 0%, transparent 100%),
    conic-gradient(
        from 200deg at 50% 35%,
        transparent 0%,
        rgba(74, 97, 179, 0.43) 30%,
        rgba(114, 71, 167, 0.72) 50%,
        rgb(65, 62, 149) 100%
      )
      30% 90%/105% 195%,
    linear-gradient(80deg, rgb(99, 71, 167) 0%, rgb(92, 62, 172) 5%, rgb(99, 127, 172) 100%);
  color: #fff;
  border-radius: 10px;
  transition: all 0.3s;
  font-weight: 700;
}

.btn--base:hover {
  transform: scale(1.1);
}
</style>
