<template>
  <section class="coffees">
    <h2>{{ filter }} Coffees</h2>
    <CoffeeCard
      v-for="coffee in filteredCoffees"
      v-if="coffees.length"
      :key="coffees.id"
      :coffee="coffee"
    />
    <div v-else>
      <h2>Error</h2>
      <p>{{ error }}</p>
    </div>
  </section>
</template>
<script>
import CoffeeCard from '@/components/CoffeeCard.vue';
export default {
  props: ['filter'],
  components: { CoffeeCard },
  data() {
    return {
      coffees: [],
      error: '',
    };
  },
  methods: {
    fetchCoffee() {
      fetch(
        'https://raw.githubusercontent.com/devchallenges-io/web-project-ideas/main/front-end-projects/data/simple-coffee-listing-data.json'
      )
        .then((res) => res.json())
        .then((data) => (this.coffees = data))
        .catch((err) => (this.error = err));
    },
  },
  mounted() {
    console.log('mounted');
    this.fetchCoffee();
  },
  computed: {
    filteredCoffees() {
      switch (this.filter) {
        case 'all':
          return this.coffees;
        case 'available':
          return this.coffees.filter((coffee) => coffee.available);
      }
    },
  },
};
</script>
<style>
h2 {
  text-transform: capitalize;
  display: none;
}

section.coffees {
  padding: 1rem 0;
  display: grid;
  gap: 3.25rem;
  /* min-height: 500px; */
}

@media screen and (min-width: 387px) {
  section.coffees {
    padding: 1.25rem 0;
  }
}

@media screen and (min-width: 1024px) {
  section.coffees {
    grid-template-columns: repeat(2, 260px);
    justify-content: center;
    column-gap: 1.5rem;
    row-gap: 3.25rem;
  }
}

@media screen and (min-width: 1280px) {
  section.coffees {
    grid-template-columns: repeat(3, 260px);
  }
}
</style>
