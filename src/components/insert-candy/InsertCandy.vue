<template>
  <div>
    <input type="text" placeholder="Candy name" ref="name" />
    <input type="text" placeholder="Candy image url" ref="image_url" />
    <input type="text" placeholder="Candy description" ref="description" />
    <button @click="handle_submit">Submit</button>
    <div v-if="candy_inserted">
      <p>Candy inserted</p>
      <p>Please, refresh the page</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  /* setting data to be used in the request */
  data() {
    return {
      candy_inserted: false,
    };
  },
  /* making a post request to insert a new candy */
  methods: {
    handle_submit() {
      if (
        this.$refs[`name`][`value`] == "" ||
        this.$refs[`image_url`][`value`] == "" ||
        this.$refs[`description`][`value`] == ""
      ) {
        alert("All inputs must be filled.");
        return;
      }
      axios
        .request({
          url: `/api/candy`,
          method: `POST`,
          /* data being sent */
          data: {
            name: this.$refs[`name`][`value`],
            image_url: this.$refs[`image_url`][`value`],
            description: this.$refs[`description`][`value`],
          },
        })
        /* on success set the variable candy_inserted to true */
        .then((response) => {
          response;
          this.candy_inserted = true;
        })
        /* on failure show a message to the user */
        .catch((error) => {
          error;
          alert("Sorry, an error occurred");
        });
    },
  },
};
</script>

<style scoped>
div {
  display: grid;
  place-items: center;
  row-gap: 20px;
  margin-top: 20px;
  margin-bottom: 50px;
}

input {
  width: 250px;
  padding: 2px;
}

button {
  border: none;
  background-image: linear-gradient(45deg, #bbd2c5, #536976, #292e49);
  width: 60px;
  height: 25px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}

button:hover {
  background-image: linear-gradient(45deg, #adb7b1, #465660, #202338);
}

button:active {
  scale: 95%;
}
</style>
