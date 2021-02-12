<template>
  <ul>
    <li>Щоб розрахувати точну вартість об`єкта потрібно додавати кожне приміщення окремо (коридор, кухня, кімната і т.д.)</li>
    <li>Вартість м<sup>2</sup> стелі залежить від сумарної площі приміщень. В акційну ціну 200 грн. входить 4 кути 1 стандартна точка світла.</li>
    <li>В вартість точки світла входить монтаж закладної(кріплення під світильник) та виведення дротів через неї. Якщо кріплення світильника більше 10см в діаметрі ціна може змінитися.</li>
    <li>Розрахунок дворівневих стель, з фотодруком і з використанням різних профілів розраховується в індивідуальному порядку.</li>
  </ul>
  <div class="web">Vanila js example is <a href="https://harpoon.lviv.ua/calc.html">here</a></div>
</template>

<script>
export default {

}
</script>

<style scoped>
  ul {
    width: 70%;
    margin: 0 auto;
    }
  .web {
    margin-top: 20px;
    color: black;
    padding: 5px;
    text-align: center;
    background-color: lightgrey;
    }
  @media screen and (max-width: 768px) {
  ul {
    width: 85%;
  }
}
</style>