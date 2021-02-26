<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloI18n msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import HelloI18n from "@/components/HelloI18n";

export default {
  name: "Home",
  components: {
    HelloI18n
  },
  created() {
    const locale = localStorage.getItem('local')
    if (locale) {
      this.$i18n.locale = locale
    }
  }
};
</script>
