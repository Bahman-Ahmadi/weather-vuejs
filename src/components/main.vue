<script>
export default {
    data () {
        return {
            inp: 'Tehran'
        }
    }
}
</script>

<template>
    <div class="box">
        <input class="location" type="text" v-model="inp">
        <router-link :to="{name: 'weather', params: {loc: inp}}"><button :disabled="inp == ''">click me</button></router-link>
    </div>
</template>

<style scoped>
    .box {
        margin: auto;
        width: fit-content;
        height: fit-content;
        top: 0;bottom: 0;left: 0;right: 0;
        position: absolute;
    }
</style>