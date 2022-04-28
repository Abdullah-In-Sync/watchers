<template>
  <h1>volume controller</h1>
  <h2>{{ volume }}</h2>
  <input type="text" v-model="movie" />
  <input type="text" v-model="movieList.title" />
  <input type="text" v-model="movieList.description" />
  <button @click="increment">Increase</button>
  <button @click="decrement">decrease</button>
  <button @click="movieData.push('warzone')">Add movie</button>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      volume: 16,
      movie: "Batman",
      movieList: {
        title: "",
        description: "",
      },
      movieData:['Superman','troy','war']
    };
  },
  computed: {},
  methods: {
    increment() {
      this.volume = this.volume + 2;
    },
    decrement() {
      this.volume = this.volume - 2;
    },
  },
  watch: {
    volume(newValue, oldValue) {
      if (newValue > oldValue && newValue == 16) {
        alert("Your volume is too high");
      }
    },

    // ==========For using immediate property ===========
    // if we put volume =16 in data then it wont work until we add handler and immediate property

    // volume:{
    //   handler(newValue){
    //   if(newValue==16){
    //     alert('Your volume is too high');
    //   }
    // },
    // immediate:true,
    // }

    // =============for using deep property ===============
    //if we have to add watchers to the nested object we have to add deep property
    movieList: {
      handler(newValue) {

        console.log(`list of movies title are:${newValue.title} and desc:${newValue.description}`);
      },
      // deep: true,
    },


    // ============for working with array, deep used ================
    movieData: {
      handler(newValue) {

        console.log(this.movieData);
      },
      deep: true,
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
