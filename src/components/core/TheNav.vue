<template>
  <nav class="bg-paper md:fixed bottom-0 text-black">
    <the-header />

    <article>
      <section>
        <FormulateInput
          v-model="selectedBrand"
          :options="brandList"
          type="select"
          placeholder="Select brand"
          label="Brand"
        />
      </section>

      <section>
        <FormulateInput
          v-model="selectedModels"
          :options="modelsList"
          type="select"
          placeholder="Select models"
          label="Models"
        />
      </section>

      <section>
        <FormulateInput
          v-model="pricesMin"
          type="number"
          label="Prices minimum"
        />

        <FormulateInput
          v-model="pricesMax"
          type="number"
          label="Prices maximum"
        />
      </section>

      <section>
        <FormulateInput
          v-model="selectedFuel"
          :options="fuelList"
          type="radio"
          label="Selected fuel:"
        />
      </section>

      <section>
        <FormulateInput
          v-model="yearsMin"
          type="number"
          label="Years minimum"
        />

        <FormulateInput
          v-model="yearsMax"
          type="number"
          label="Years maximum"
        />
      </section>

      <section>
        <FormulateInput
          v-model="milesMin"
          type="number"
          label="Miles minimum"
        />

        <FormulateInput
          v-model="milesMax"
          type="number"
          label="Miles maximum"
        />
      </section>

      <!--
      <section>
        <select name="brands">
          <option value="">Citroen</option>
          <option value="">Peugeot</option>
          <option value="">Renault</option>
          <option value="">Ford</option>
          <option value="">Nissan</option>
          <option value="">Suzuki</option>
          <option value="">Hyundai</option>
        </select>
      </section>

      <section>
        <select name="models">
          <option value="">Citroen</option>
          <option value="">Peugeot</option>
          <option value="">Renault</option>
          <option value="">Ford</option>
          <option value="">Nissan</option>
          <option value="">Suzuki</option>
          <option value="">Hyundai</option>
        </select>
      </section>
      -->
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

    milesMin: 0,

    milesMax: 100000,
  }),
}
</script>

<style scoped>
nav {
  height: 100vh;
}

@screen md {
  nav {
    width: 400px;
  }
}
</style>
