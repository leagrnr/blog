<script>
import { HeartIcon} from '@heroicons/vue/24/solid';
export default {

  components: { HeartIcon },

  data () {
    return {
      postList: []
    }
  },

  methods: {
    addLike(post) {
      if (!post.likes) {
        post.likes = 1
      } else {
        post.likes++
      }
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
  <div class="result">
    <div class="card" v-for="post in postList" :key="post.id">
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
      <div class="footer">
        <button v-on:click="addLike(post)"> <heart-icon class="icon"/> </button>
        <div class="likes"> {{ post.likes ? post.likes: 0 }} Like{{ post.likes && post.likes>1 ? "s" : ""}}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.result {
  display: flex;
  flex-wrap: wrap;
}

.card {
  width: 31%;
  box-sizing: border-box;
  border: 1px solid #aaa;
  padding: 5px;
  margin: 1%;
}

.card h3:first-letter, .card p:first-letter {
  text-transform: capitalize;
}

.card h3 {
  margin: 0;
  color: darkorchid ;
  font-weight: 700;
  font-size: 16px;
}

.card p {
  font-size: 14px;
}

.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top:10px
}

.likes {
  display: flex;
}

.icon {
  height: 20px;
  color: #f8f8f8;
}

button {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  margin: 0;
  outline: none;
}
</style>
