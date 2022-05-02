<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">Ronald Ulysses Swanson</span>
          <span class="subtitle">The Man. The Myth. The Legend.</span>
        </h1>

        <h1 class="title">Famous Quotes</h1>
        <button class="button is-success is-rounded" v-on:click="fetch">
          Consultar
        </button>
      </div>
    </div>

    <div class="container">
      <div
        class="columns is-desktop is-mobile is-tablet is-multiline is-centered"
      >
        <div
          class="column is-12-mobile.is-4-desktop is-4-tablet"
          v-for="quote of quotes"
          v-bind:key="quote.id"
        >
          <div class="card">
            <div class="card-header"><img src="./assets/swanson2.PNG" alt="" /></div>
            <div class="card-content">
              <h3 class="title is-size-4">{{ quote }}</h3>
              <button class="button is-success is-rounded is-small">
                Read more
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!--<div v-for="quote of quotes" v-bind:key="quote.id">
      {{ quote }}
    </div>-->
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data: function () {
    return {
      quotes: [],
    };
  },
  methods: {
    fetch() {
      let result = axios
        .get("https://ron-swanson-quotes.herokuapp.com/v2/quotes/search/%20")
        .then((response) => {
          this.quotes = response.data;
          console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
      console.log("hola món");
    },
  },
};
</script>