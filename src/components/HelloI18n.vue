<template>
  <div>
    <p>{{ $t("hello", { name }) }}</p>
    <p>{{ $t("goodbye") }}</p>

    <p>{{ $tc("car", 1) }}</p>
    <p>{{ $tc("car", 5) }}</p>

    <p>{{ $tc("person", 0) }}</p>
    <p>{{ $tc("person", 1) }}</p>
    <p>{{ $tc("person", 5) }}</p>

    <p>{{ $d(new Date(), "short") }}</p>
    <p>{{ $d(new Date(), "short", "en-GB") }}</p>
    <p>{{ $d(new Date(), "long") }}</p>
    <p>{{ $d(new Date(), "long", "en-GB") }}</p>



    <button @click="setLocale('en')" class="button">English</button>
    <button @click="setLocale('es')" class="button">Spanish</button>
    <button @click="setLocale('de')" class="button">German</button>




  </div>
</template>
<script>
export default {
  name: "HelloI18n",
  data() {
    return {
      name: "Stonyx"

    }
  },
  methods: {
    setLocale(locale) {
      this.$i18n.locale = locale;
      localStorage.setItem("locale", locale);
    }
  }
};
</script>
