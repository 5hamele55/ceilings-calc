<template>
    <h1>Розрахунок вастості стелі </h1>
        <Inputs />
    <hr>
    <Info />
</template>
<script>
import Inputs from './Inputs.vue';
import Info from './Info.vue';

export default {
    components : {
        Inputs,  Info
    },
    setup() {
            
        return {
        }
    }
}
</script>
<style scoped>
h1 {
    padding: 20px;
    text-align: center;
}
hr {
    width: 90%;
    height: 1px;
    background-color: lightgrey;
    margin: 20px auto;
    border: 0;
}
</style>