<template>
  <Navbar />
  <router-view/>
  <Footer />
</template>

<style>

</style>

<script>
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";

export default {
  name: "App",
  components: {
    Footer,
    Navbar
  }
}

</script>