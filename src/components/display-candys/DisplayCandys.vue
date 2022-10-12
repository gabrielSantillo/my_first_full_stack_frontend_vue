<template>
    <div>
        <h1>Candys</h1>
            <section v-for="candy in candys" :key="candy[`id`]">
                <h1>{{candy[0]}}</h1>
                <img :src="candy[1]" alt="">
                <p>{{candy[2]}}</p>
                <button :id="candy[3]">Delete</button>
            </section>

    </div>
</template>

<script>
import axios from "axios"
    export default {
        data() {
            return {
                candys: []
            }
        },
        mounted () {
            axios.request({
                url: `http://127.0.0.1:5000/api/candy`
            }).then((response) => {
                this.candys = response[`data`]
            }).catch((error) => {
                error
            });
        },
    }
</script>

<style lang="scss" scoped>

</style>