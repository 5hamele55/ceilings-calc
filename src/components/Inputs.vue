<template>
    <form>
        <div class="inputs">
            <label>Назва приміщення<br><input type="text" v-model="room.name" placeholder="Коридор"></label>
            <label>Площа м<sup>2</sup><br><input type="number" v-model="room.square"></label>
            <label>Периметр м/п<br><input type="number" v-model="room.perimeter"></label>
            <label>Кути шт.<br><input type="number" v-model="room.corners"></label>
            <label>т. світла шт.<br><input type="number" v-model="room.lamps"></label>
            <label>Криві м/п<br><input type="number" v-model="room.curves"></label>
            <button @click.prevent="addRoom()" :disabled ="roomArr.some(item=> !item)">Додати</button>
        </div>
        <div class="output">
            <ul>
                <li v-for="(r, index) in roomGroup" :key="r">{{ r }} <button class="deleteRoom" @click.prevent="removeRoom(index)">&times;</button></li>
            </ul>
            <div class="total">
                <Radio @fff="emitTape" />
                <div class="totalOutput">Площа: {{total(1)}} м<sup>2</sup>, Периметр: {{total(2)}} м/п, дод. кути: {{(total(3)-(4*roomGroup.length))}} шт., дод. т.світла: {{(total(4)-(roomGroup.length))}} шт., Криві: {{total(5)}} м/п</div>
                <div class="totalSum">{{ calculator() }} грн.</div>
            </div>
        </div>
    </form>
</template>

<script>
import { computed, reactive, ref } from 'vue'
import Radio from './Radio'
export default {
    components: {
        Radio
    },
    setup() {
        const room = reactive({
            name: "",
            square: "0",
            perimeter: "0",
            corners: "4",
            lamps: "1",
            curves: "0"
        })
        const roomArr = computed((i) => {
            i = Object.values(room)
           return i
        })
        const roomGroup = ref([]);
        const tapePrice = ref(0);
        const emitTape = val => {
            tapePrice.value = val;
            return tapePrice;
        }
        
        const total = function (index) {
            let arr = [];
            let result;
            for (let item of roomGroup.value)
            arr.push(+item[index]);
            result = arr.reduce(function(sum, current) {
                return sum + current;
            }, 0);
            return result;
        }
        const addRoom = () => {
            roomGroup.value.push(roomArr.value)
            room.name = "",
            room.square = "0",
            room.perimeter = "0",
            room.corners = "4",
            room.lamps = "1",
            room.curves = "0"
        }
        const calculator = () => {
            let sum = Number;
            let counter = 0;
            if (total(1) >= 100) {
                counter = total(1)*190;
            }
            else if (total(1) >= 30) {
                counter = total(1)*200;
            }
            else if (total(1) > 20) {
                counter = total(0)*230;
            }
            else if (total(1) > 15) {
                counter = total(0)*250;
            }
            else if (total(1) >= 10) {
                counter = total(1)*270;
            }
            else if (total(1) < 10 && total(1) > 0) {
                counter = 2700;
            }

            sum = counter+(total(2)*tapePrice.value)+((total(3)-(4*roomGroup.value.length))*40)+
            ((total(4)-(roomGroup.value.length))*90)+(total(5)*80);
            return sum;
        }
        const removeRoom = function(index) {
            roomGroup.value.splice(index, 1);
            }
        return {
            roomArr, roomGroup, room, total, addRoom, tapePrice, calculator, removeRoom, emitTape
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        justify-content: space-around;
        margin: 0 auto;
        width: 70%;
    }
    .inputs {
        width: 45%;
        display: flex;
        flex-direction: column;
    }
    .inputs input, button {
        box-sizing: border-box;
        width: 95%;
        border-radius: 5px;
        border: none;
        outline: none;
        line-height: 30px;
        text-align: center;
    }
    button {
        margin-top: 10px;
    }
    button:active {
        background-color:#0083b0;
        color: white;
        border: 1px solid white;
    }
    .inputs input:focus {
        border: 1px solid black;
    }
    .inputs label {
        font-size: 14px;
    }
    .output {
        width: 55%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-left: 10px;
    }
    .output ul li {
        list-style: none;
        display: flex;
        justify-content: space-between;
    }
    .total {
        display: flex;
        flex-direction: column;
    }
    .totalOutput, .totalSum {
        text-align: center;
        padding: 5px;
        margin-top: 5px;
        vertical-align: middle;
        min-height: 30px;
        border-radius: 5px;
        background-color:white;
        color: black;
        font-size: 14px;
    }
    .totalSum {
        line-height: 30px;
    }
    .deleteRoom {
        width: 16px;
        height: 16px;
        text-align: center;
        line-height: 16px;
        font-size: 16px;
        border-radius: 50%;
        color: black;
        background-color: white;
        cursor: pointer;
        margin-right: 3px;
}
    .deleteRoom:active {
        border: 0.5px solid black;
}
@media screen and (max-width: 768px) {
  form {
    width: 90%;
  }
}
</style>