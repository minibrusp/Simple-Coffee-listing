<template>
  <header>
    <div class="hero">
      <img src="../assets/bg-cafe.jpg" alt="hero image" />
    </div>
  </header>
</template>
<script>
export default {};
</script>

<style scoped>
header img {
  width: 100%;
  /* min-height: 200px; */
  display: block;
  aspect-ratio: 16 / 9;
}

@media screen and (min-width: 387px) {
  header div {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  }

  header img {
    max-height: 300px;
    width: 100%;
  }
}
</style>
