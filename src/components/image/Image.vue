<!-- eslint-disable vue/multi-word-component-names -->
<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'

type ActiveWheelType = {
  id: number
  clicked: boolean
}

export default defineComponent({
  props: {
    src: {
      type: String as PropType<string>,
      required: true
    },
    alt: {
      type: String as PropType<string>,
      required: true
    },
    active: {
      type: Object as PropType<ActiveWheelType>,
      required: true
    }
  },
  setup(props) {
    return {
      imgSrc: props.src,
      imgAlt: props.alt,
      imgActive: props.active
    }
  }
})
</script>

<template>
  <img :class="['image', { 'image--rotate': active && active.clicked }]" :src="src" :alt="alt" />
</template>

<style scoped>
.image {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.image--rotate {
  animation: rotate 5s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
