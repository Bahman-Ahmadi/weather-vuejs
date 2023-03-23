<script>
    import axios from 'axios';

    export default {
        data () {
            return {
                loc: this.$route.params.loc,
                data: {
                    main: {temp: 0},
                    weather: [{main: 'Unknown'}]
                }
            }
        },
        mounted() {
            var CITY = this.$route.params.loc;
            var API_KEY = '';
            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${CITY}&appid=${API_KEY}`).then((resp) => {
                console.log(resp);
                this.$data.data = resp.data;
            });
        }
    }
</script>
<template>
    <div class="loc">{{loc}}</div>
    <div class="temp">{{Math.floor(data.main.temp) - 273}} °C</div>
    <div class="temp">{{Math.floor(data.main.temp)}} °K</div>
    <div class="status">{{data.weather[0].main}}</div>
</template>
<style scoped>
    .loc, .temp, .status {
        width: 100%;
        height: 3rem;
        border-radius: 0.5rem;
        background: var(--color-background-soft);
        margin: 7px auto;
        text-align: center;
        padding: 7px;
    }
    .status {
        font-size: 20px;
    }
</style>