<template>
  <nav
    class="bg-paper md:fixed bottom-0 text-black rounded-br-3xl rounded-tr-3xl"
  >
    <the-header />

    <article class="grid gap-y-3 px-7">
      <section class="grid grid-cols-12 gap-x-5 gap-y-2">
        <div class="col-span-12">
          <h4>Cars</h4>
        </div>

        <div class="col-span-6">
          <FormulateInput
            v-model="selectedBrand"
            :options="brandList"
            type="select"
            placeholder="Select brand"
            label="Brand"
          />
        </div>

        <div class="col-span-6">
          <FormulateInput
            v-model="selectedModels"
            :options="modelsList"
            type="select"
            placeholder="Select models"
            label="Models"
          />
        </div>
      </section>

      <section class="grid grid-cols-12 gap-x-5 gap-y-2">
        <div class="col-span-12">
          <h4>Prices</h4>
        </div>

        <div class="col-span-6">
          <FormulateInput v-model="pricesMin" type="number" label="Minimum" />
        </div>

        <div class="col-span-6">
          <FormulateInput v-model="pricesMax" type="number" label="Maximum" />
        </div>
      </section>

      <section class="grid grid-cols-12 gap-x-5 gap-y-2">
        <div class="col-span-12">
          <h4>Selected fuel</h4>
        </div>

        <div class="col-span-12 mt-2">
          <FormulateInput
            v-model="selectedFuel"
            :options="fuelList"
            type="radio"
          />
        </div>
      </section>

      <section class="grid grid-cols-12 gap-x-5 gap-y-2">
        <div class="col-span-12">
          <h4>Years</h4>
        </div>

        <div class="col-span-6">
          <FormulateInput v-model="yearsMin" type="number" label="Minimum" />
        </div>

        <div class="col-span-6">
          <FormulateInput v-model="yearsMax" type="number" label="Maximum" />
        </div>
      </section>

      <section class="grid grid-cols-12 gap-x-5 gap-y-2">
        <div class="col-span-12">
          <h4>Kilometers</h4>
        </div>

        <div class="col-span-6">
          <FormulateInput
            v-model="kilometersMin"
            type="number"
            label="Minimum"
          />
        </div>

        <div class="col-span-6">
          <FormulateInput
            v-model="kilometersMax"
            type="number"
            label="Maximum"
          />
        </div>
      </section>
    </article>
  </nav>
</template>

<script>
import TheHeader from '@/components/core/TheHeader'

export default {
  name: 'TheNav',

  components: { TheHeader },

  props: {
    brandListFilters: {
      type: Array,
      required: true,
    },
  },

  data: () => ({
    selectedBrand: 'Suzuki',

    brandList: {
      suzuki: 'Suzuki',
      peugeot: 'Peugeot',
      renault: 'Renault',
      citroen: 'Citroen',
      nissan: 'Nissan',
      ford: 'Ford',
      hyundai: 'Hyundai',
      volkswagen: 'Volkswagen',
    },

    selectedModels: 'Vitara',

    modelsList: {
      vitara: 'Vitara',
      ignis: 'Ignis',
      berlingo: 'Berlingo',
      clio: 'Clio',
      capture: 'Capture',
      astra: 'Astra',
      corsa: 'Corsa',
    },

    pricesMin: 0,

    pricesMax: 100000,

    selectedFuel: '',

    fuelList: {
      essence: 'Essence',
      diesel: 'Diesel',
      hybride: 'Hybride',
      electrique: 'Electrique',
    },

    yearsMin: 0,

    yearsMax: 2021,

    kilometersMin: 0,

    kilometersMax: 100000,
  }),
}
</script>

<style lang="scss" scoped>
nav {
  height: 100vh;
}

@screen md {
  nav {
    width: 400px;
  }
}
</style>
