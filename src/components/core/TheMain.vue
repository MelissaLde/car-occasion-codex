<template>
  <main class="bg-background p-10">
    <v-car-card
      v-for="car in carList"
      :key="car.id"
      :brand="car.brand"
      :model="car.model"
      :image="car.image"
    />
  </main>
</template>

<script>
import VCarCard from '@/components/commons/VCarCard'
import '@/assets/global.css'

export default {
  name: 'TheMain',

  components: { VCarCard },

  props: {
    carList: {
      type: Array,
      required: true,
    },
  },
}
</script>
