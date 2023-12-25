<template>
  <section v-if="coffee" :key="coffee.id" class="coffee">
    <div class="coffee_header">
      <span v-if="coffee.popular">Popular</span>
      <img :src="coffee.image" :alt="coffee.name" />
    </div>
    <div class="coffee_details">
      <div class="coffee_details_top">
        <h3>{{ coffee.name }}</h3>
        <p>{{ coffee.price }}</p>
      </div>
      <div class="coffee_details_bottom">
        <div v-if="coffee.rating" class="votes_container">
          <img src="../assets/Star_fill.svg" alt="start" />
          <p>
            <span class="rating">{{ coffee.rating }}</span>
            <span class="votes">({{ coffee.votes }} votes)</span>
          </p>
        </div>
        <div v-else class="votes_container">
          <img src="../assets/Star.svg" alt="start" />
          <p>No ratings</p>
        </div>
        <p v-if="!coffee.available" class="sold-out">Sold out</p>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  props: ['coffee'],
};
</script>
<style>
section.coffee {
  max-width: 260px;
  margin: 0 auto;
  opacity: 1;
  transition: opacity 0.5s ease;
  animation: fadeIn 1s ease;
}

/* .coffee_header  */
section.coffee .coffee_header {
  display: block;
  position: relative;
  overflow: hidden;
  border-radius: 15px;
}

section.coffee .coffee_header span {
  display: block;
  position: absolute;
  top: 0.5rem;
  left: 0.5rem;
  font-size: 0.625rem;
  font-weight: 700;
  background-color: var(--grandis);
  padding: 4px 10px;
  border-radius: 10px;
  color: var(--light-black-pearl);

  z-index: 5;
}

section.coffee .coffee_header img {
  width: 100%;
  border-radius: 15px;
  display: block;

  transition: transform 1s ease;
}

section.coffee:hover .coffee_header img {
  transform: scale(1.1);
}

/* coffee_details  */
section.coffee .coffee_details {
  padding: 0.7rem 0;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
  width: 100%;
}

section.coffee .coffee_details p {
  margin: 0;
}

/* coffee_details_top */
section.coffee .coffee_details .coffee_details_top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

section.coffee .coffee_details .coffee_details_top h3 {
  color: var(--floral-white);
  font-size: 1rem;
  margin: 0;
}

section.coffee .coffee_details .coffee_details_top p {
  color: var(--floral-white);
  font-size: 0.75rem;
  padding: 4px 7px;
  background-color: var(--granny-apple);
  color: var(--light-black-pearl);
  font-weight: 700;
  border-radius: 5px;
}

/* coffee_details_bottom */
section.coffee .coffee_details .coffee_details_bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.875rem;
  font-weight: 700;
  width: 100%;
}

section.coffee .coffee_details .coffee_details_bottom .votes_container {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 0.25rem;
}

section.coffee .coffee_details .coffee_details_bottom .votes_container .rating {
  color: var(--floral-white);
  margin-right: 0.25rem;
}

section.coffee .coffee_details .coffee_details_bottom .sold-out {
  color: var(--terra-cota);
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
