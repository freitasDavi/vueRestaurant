<template>
  <Banner />
  <div class="main_container">
    <h1>Monte o seu burger</h1>
    <BurgerForm />
  </div>
</template>

<script>
import Banner from '../components/Banner';
import BurgerForm from "@/components/BurgerForm";

export default {
  name: 'Home',
  components: {
    BurgerForm,
    Banner
  }
}
</script>
