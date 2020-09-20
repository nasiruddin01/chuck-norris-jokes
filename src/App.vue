 <template>
  <div id="app">
    <div class="container">
      <h1>The Random Jokes</h1>
      <img alt="Vue logo" src="./assets/bg.png" />
      <button class="btn" @click="fetchRandomJoke()">Get Jokes</button>
      <p>{{ currentJoke }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_RANDOM_JOKE_ENDPOINT = "https://api.chucknorris.io/jokes/random";
export default {
  name: "app",

  mounted() {
    this.fetchRandomJoke();
  },
  data: function () {
    return {
      currentJoke: null,
    };
  },
  methods: {
    fetchRandomJoke() {
      console.log("fetching");
      axios.get(API_RANDOM_JOKE_ENDPOINT).then((response) => {
        this.currentJoke = response.data.value;
      });
    },
  },
};
</script>




<style >
@import url("https://fonts.googleapis.com/css2?family=Kufam:ital,wght@0,400;0,500;1,400;1,500&family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;1,200;1,300;1,400;1,600&display=swap");
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: "Source Sans Pro", sans-serif;
  font-size: 1.2rem;
  overflow: hidden;
}
h1 {
  font-family: "Kufam", cursive;

}
p {
  width: 620px;
  text-align: center;

}
.container .btn {
  -moz-box-shadow: inset 0px 1px 6px 0px #97c4fe;
  -webkit-box-shadow: inset 0px 1px 6px 0px #97c4fe;
  box-shadow: inset 0px 1px 6px 0px #97c4fe;
  background-color: #3d94f6;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
  display: inline-block;
  color: #ffffff;
  font-family: arial;
  font-size: 15px;
  font-weight: bold;
  padding: 16px 64px;
  text-decoration: none;
  text-shadow: 1px 1px 5px #1570cd;
  margin-top: 1rem;
  font-family: "Kufam", cursive;
  font-size: 1.5rem;
}
.container .btn:hover {
  background-color: #1e62d0;
}
.container .btn:active {
  position: relative;
  top: 1px;
}
@media (max-width: 580px) {
  .container {
    margin-top: 6rem;
    overflow: hidden;
  }
  .container img {
    max-width: 100vw;
  }
  p {
    width: 100vw;
    text-align: center;
  }
  h1{
    font-size: 2rem;
  }
}
</style>
