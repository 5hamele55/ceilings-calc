<template>
<div class="output">
    <ul>
        <li>{{ room.name }}, {{ room.square }}, {{ room.perimeter }}, {{ room.corners }}, {{ room.lamps }}, {{room.curves}}</li>
    </ul>
    <div class="total">
        <label for=""><input type="radio" name="tape" id="noTape" checked>Без вставки</label>
        <label for=""><input type="radio" name="tape" id="whiteTape">Зі вставкою</label>
        <label for=""><input type="radio" name="tape" id="colorTape">З кольоровою вставкою</label>
        <div class="totalOutput">Площа: 0 м<sup>2</sup>, Периметр: 0 м/п,<br> дод. кути: 0 шт.,<br> дод.
                т.світла: 0 шт., Криві: 0 м/п</div>
        <div class="totalSum">1231 грн.</div>
    </div>
</div>
</template>

<script>
export default {
    props: {
    room: Array
},
    setup() {
        
    }
}
</script>

<style scoped>
    .output {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .output ul li {
        list-style: none;
    }
    .total {
        display: flex;
        flex-direction: column;
    }
    .totalOutput, .totalSum {
        text-align: center;
        padding: 5px;
        margin: 5px;
        vertical-align: middle;
        min-height: 30px;
        min-width: 200px;
        border-radius: 5px;
        background-color:white;
        color: black;
    }
    .totalSum {
        line-height: 30px;
    }
</style>