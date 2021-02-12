<template>
    <label><input type="radio" name="tape" v-model="tapePrice" value="0" checked @change="emitTape">Без вставки</label>
    <label><input type="radio" name="tape" v-model="tapePrice" value="40" @change="emitTape">Зі вставкою</label>
    <label><input type="radio" name="tape" v-model="tapePrice" value="60" @change="emitTape">З кольоровою вставкою</label>
</template>

<script>
import { ref, onMounted } from 'vue'
export default {
    emits: ['fff'],
setup(props, { emit }) {
    const tapePrice = ref(0);

    const emitTape = () => emit("fff", tapePrice.value)
    const qq = onMounted(() => {
        emitTape()
    });
return {
    tapePrice, emitTape, qq
}
}
}
</script>

<style>

</style>