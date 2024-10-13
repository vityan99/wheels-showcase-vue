<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable vue/no-reserved-component-names -->
<!-- eslint-disable vue/multi-word-component-names -->
<script lang="ts">
import { defineComponent, reactive } from 'vue'
import type { PropType } from 'vue'

import Image from '../image/Image.vue'
import Button from '../button/Button.vue'

interface IWheelsConfig {
  id: number
  key: number
  src: string
  alt: string
  title: string
}

type WheelsConfigType = IWheelsConfig[]

export default defineComponent({
  props: {
    config: {
      type: Array as PropType<WheelsConfigType>,
      required: true
    }
  },
  components: {
    Image,
    Button
  },
  setup(props) {
    const state = reactive({
      activeWheels: props.config.map((wheel) => ({ id: wheel.id, clicked: false })),
      setActiveWheel: (id: number) => {
        const wheel = state.activeWheels.find((wheel) => wheel.id === id)

        if (wheel) {
          wheel.clicked = !wheel.clicked
        }
      }
    })

    return {
      wheelConfig: props.config,
      state
    }
  }
})
</script>

<template>
  <div class="wheels">
    <div class="wheels__container">
      <div class="wheels__img-wrapper" v-for="wheel in wheelConfig" :key="wheel.id">
        <Image
          :id="wheel.id"
          :src="wheel.src"
          :alt="wheel.alt"
          :active="
            state.activeWheels.find((activeWheel) => activeWheel.id === wheel.id) || {
              id: wheel.id,
              clicked: false
            }
          "
        />
      </div>
    </div>
    <div class="wheels__controllers">
      <Button
        v-for="wheel in wheelConfig"
        :key="wheel.id"
        :title="wheel.title"
        :id="wheel.id"
        :clickHandler="state.setActiveWheel"
      />
    </div>
  </div>
</template>

<style scoped>
.wheels {
  width: 700px;
  min-height: 100px;
  background-color: #fff;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 auto;
  padding: 30px;
  margin-bottom: 50px;
}

.wheels__container {
  display: flex;
  justify-content: space-between;
  width: 600px;
  margin-bottom: 30px;
}

.wheels__img-wrapper {
  width: 170px;
  height: 170px;
}

.wheels__controllers {
  display: flex;
  justify-content: space-between;
  width: 540px;
  margin-bottom: 15px;
}
</style>
