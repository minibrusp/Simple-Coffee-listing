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
  padding: 1rem;
  padding-top: 3rem;
  background-color: var(--light-black-pearl);
  position: relative;

  background-image: url(../assets/vector.svg);
  background-repeat: no-repeat;
  background-position: calc(100% + 3.9rem) calc(0% + 1rem);

  max-width: 387px;
  margin: 0 auto;

  margin-bottom: 3rem;
}

h1 {
  font-size: 2rem;
  color: var(--floral-white);
  margin: 0;
}

article header p {
  font-weight: 600;
  max-width: 325px;
  margin: 0.55rem auto;
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

  transition: background 0.5s ease;
}

.controls input:checked ~ span {
  background: var(--raven);
}

@media screen and (min-width: 387px) {
  article {
    margin-top: 10rem;
    border-radius: 13px;
    padding: 6.7rem 1rem 2.5rem 1rem;

    background-position: calc(100% + 3.9rem) calc(0% + 3rem);

    margin-bottom: 3rem;

    min-height: 80vh;
  }

  .controls {
    margin: 1.25rem 0;
  }
}

@media screen and (min-width: 1024px) {
  article {
    max-width: 712px;

    padding: 5rem 1rem 2.5rem 1rem;

    background-position: calc(78.5% + 0rem) calc(1.25% + 0rem);
  }

  article header p {
    font-weight: 600;
    max-width: 500px;
    margin: 0.55rem auto;
  }
}

@media screen and (min-width: 1280px) {
  article {
    max-width: 1094px;

    padding: 5rem 1rem 2.5rem 1rem;

    background-position: calc(65.5% + 0rem) calc(2.25% + 0rem);
  }
}
</style>
