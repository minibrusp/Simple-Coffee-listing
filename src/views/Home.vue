<template>
  <article>
    <header>
      <h1>Our Collection</h1>
      <p>
        Introducing our Coffee Collection, a selection of unique coffees from
        different roast types and origins, expertly roasted in small batches and
        shipped fresh weekly.
      </p>

      <div class="controls">
        <label>
          <input type="radio" value="all" v-model="filter" />
          <span>All Products</span>
        </label>
        <label>
          <input type="radio" value="available" v-model="filter" />
          <span>Available Now</span>
        </label>
      </div>
    </header>
    <Coffees :filter="filter" />
  </article>
</template>

<script>
import router from '@/router';
import Coffees from '@/components/Coffees.vue';

// @ is an alias to /src

export default {
  name: 'Home',
  components: { Coffees },
  data() {
    return {
      filter: 'all',
    };
  },
  methods: {
    setFilterSearchParams() {
      router.push({ path: '/', query: { filter: this.filter } });
    },
  },
  mounted() {
    this.setFilterSearchParams();
  },
  updated() {
    this.setFilterSearchParams();
  },
};
</script>

<style>
article {
  text-align: center;
  padding: 1rem 1.9rem;
  padding-top: 3rem;
  background-color: var(--light-black-pearl);
  position: relative;

  background-image: url(../assets/vector.svg);
  background-repeat: no-repeat;
  background-position: calc(100% + 3.9rem) calc(0% + 1rem);
}

h1 {
  font-size: 2rem;
  color: var(--floral-white);
  margin: 0;
}

.controls {
  margin: 1rem 0;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

.controls input {
  display: none;
}

.controls span {
  color: var(--floral-white);
  cursor: pointer;
  display: block;
  font-size: 0.875rem;
  padding: 0.5rem 0.7rem;
  border-radius: 9px;
  font-weight: 600;
}

.controls input:checked ~ span {
  background: var(--raven);
}
</style>
