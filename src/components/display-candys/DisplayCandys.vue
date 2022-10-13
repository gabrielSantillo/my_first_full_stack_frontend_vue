<template>
  <div>
    <div class="candys_container">
      <section v-for="candy in candys" :key="candy[`id`]">
        <h1>{{ candy[0] }}</h1>
        <img :src="candy[1]" class="image" />
        <p>{{ candy[2] }}</p>
        <button>Delete</button>
      </section>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      candys: [],
    };
  },
  mounted() {
    axios
      .request({
        url: `http://127.0.0.1:5000/api/candy`,
      })
      .then((response) => {
        this.candys = response[`data`];
      })
      .catch((error) => {
        error;
      });
  },
};
</script>

<style scoped>
.candys_container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  place-items: center;
  text-align: center;
}

img {
  width: 250px;
  height: 250px;
  object-fit: cover;
  border-radius: 5px;
}

button {
  width: 70px;
  height: 25px;
  justify-self: center;
  margin-top: 15px;
  border: none;
  background-color: rgb(219, 87, 87);
  color: white;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: rgb(210, 106, 106);
}

button:active {
  scale: 95%;
}
</style>
