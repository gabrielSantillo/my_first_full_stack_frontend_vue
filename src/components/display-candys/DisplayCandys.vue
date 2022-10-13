<template>
  <div class="container">
    <div v-if="candy_deleted" class="candy_deleted_container">
      <p>Candy deleted</p>
      <p>Please, refresh the page</p>
    </div>
    <div class="candys_container">
      <section v-for="candy in candys" :key="candy[`id`]">
        <h1>{{ candy[0] }}</h1>
        <img :src="candy[1]" class="image" />
        <p>{{ candy[2] }}</p>
        <button @click="handle_delete(candy, $event)">Delete</button>
      </section>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  methods: {
    handle_delete(candy) {
      axios
        .request({
          url: `http://127.0.0.1:5000/api/candy`,
          method: `DELETE`,
          data: {
            candy_id: candy[3],
          },
        })
        .then((success) => {
          success;
          this.candy_deleted = true;
        })
        .catch((error) => {
          error;
        });
      candy;
    },
  },
  data() {
    return {
      candys: [],
      candy_deleted: false,
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

.candy_deleted_container {
    font-size: 1.2rem;
    font-weight: bold;
    color: rgb(2, 179, 137);
    border: 2px solid black;
    border-radius: 5px;
    width: 250px;
    justify-self: center;
    text-align: center;
}

.container {
    display: grid;
}
</style>
