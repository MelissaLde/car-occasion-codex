<template>
  <nav class="bg-paper md:fixed bottom-0">
    <article>
      <section>
        <div v-for="brand in brandListFilters" :key="brand.id">
          <input type="checkbox" name="Peugeot" />
          <label> {{ brand.name }}</label>
          <i>({{ brand.announcement }})</i>
        </div>
      </section>

      <section>
        <select name="">
          <option value="">Pro</option>
          <option value="">Particulier</option>
        </select>
      </section>
    </article>
  </nav>
</template>

<script>
export default {
  name: 'TheNav',

  props: {
    brandListFilters: {
      type: Array,
      required: true,
    },
  },
}
</script>
