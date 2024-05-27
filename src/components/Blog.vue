<script>
export default {

  data () {
    return {
      postList: [],
    }
  },

  methods: {
    maFonction(e) {
      console.log(e);
    }

  },

  mounted() {
    // Method exécutée au chargement de la page
    fetch('https://jsonplaceholder.typicode.com/posts')
        .then(response => response.json())
        .then(json => this.postList = json);

    console.log(this.postList);
  }

}

</script>

<template>
  {{ postList }}
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
