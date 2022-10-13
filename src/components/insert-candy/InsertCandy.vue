<template>
  <div>
    <input type="text" placeholder="Candy name" ref="name"/>
    <input type="text" placeholder="Candy image url" ref="image_url"/>
    <input type="text" placeholder="Candy description" ref="description"/>
    <button @click="handle_submit">Submit</button>
    <div v-if="candy_inserted">
        <p>Candy inserted</p>
    </div>
  </div>
</template>

<script>
import axios from "axios"
export default {

    data() {
        return {
            candy_inserted: false
        }
    },
    methods: {
        handle_submit() {
            axios.request({
                url: `http://127.0.0.1:5000/api/candy`,
                method: `POST`,
                data: {
                    name: this.$refs[`name`][`value`],
                    image_url: this.$refs[`image_url`][`value`],
                    description: this.$refs[`description`][`value`]
                }
            }).then((response) => {
                response
                this.candy_inserted = true
            }).catch((error) => {
                error
            })
        }
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
