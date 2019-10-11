<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <h1>Welcome to Your Vue.js App</h1>
        <HelloWorld quote="this is the quote" author="roel"></HelloWorld>
    </div>
</template>

<script lang="ts">
    
    import HelloWorld from '@/components/HelloWorld.vue';
    import { Component, Vue } from 'vue-property-decorator';
    
    export default {
        name:"app",
        components: { HelloWorld },
    };
    
</script>
