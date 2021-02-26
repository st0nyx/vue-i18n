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

    <p>{{ $n(100, "currency") }}</p>

    <p>{{ product.name }}: {{ $n(product.price, "currency") }}</p>
    <p>{{ product.stock }} left in stock</p>

    <div>
      <i18n-n :value="4567.45" format="currency">
        <template v-slot:currency="slotProps">
          <span style="color: red; font-size: 25px; font-weight: bold">{{
            slotProps.currency
          }}</span>
        </template>
        <template v-slot:integer="slotProps">
          <span style="color:red; font-size:25px">{{ slotProps.integer }}</span>
        </template>
        <template v-slot:decimal="slotProps">
          <span style="color:blue">{{ slotProps.decimal }}</span>
        </template>
        <template v-slot:fraction="slotProps">
          <span style="color:purple">{{ slotProps.fraction }}</span>
        </template>
        <template v-slot:group="slotProps">
          <span style="color:red; font-size:25px">{{ slotProps.group }}</span>
        </template>
      </i18n-n>
    </div>

    <button @click="setLocale('en-GB')" class="button">UK</button>
    <button @click="setLocale('en-US')" class="button">USA</button>
    <button @click="setLocale('es-ES')" class="button">German</button>
  </div>
</template>
<script>
const products = {
  "en-GB": {
    name: "Red Jeans",
    stock: 4,
    price: 89
  },
  "en-US": {
    name: "Red Jeans",
    stock: 2,
    price: 109
  },
  "es-ES": {
    name: "Vaqueros Rojos",
    stock: 9,
    price: 99
  }
};

export default {
  name: "HelloI18n",
  data() {
    return {
      name: "Stonyx"
    };
  },
  methods: {
    setLocale(locale) {
      this.$i18n.locale = locale;
      localStorage.setItem("locale", locale);
    }
  },
  computed: {
    product() {
      return products[this.$i18n.locale];
    }
  }
};
</script>
