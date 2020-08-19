<template>
    <div class="calculator">
        <div class="display">647654</div>
        <div class="btn">AC</div>
        <div class="btn">+/-</div>
        <div class="btn">%</div>
        <div class="operator btn">/</div>
        <div class="btn">7</div>
        <div class="btn">8</div>
        <div class="btn">9</div>
        <div class="operator btn">x</div>
        <div class="btn">4</div>
        <div class="btn">5</div>
        <div class="btn">6</div>
        <div class="operator btn">-</div>
        <div class="btn">1</div>
        <div class="btn">2</div>
        <div class="btn">3</div>
        <div class="operator btn">+</div>
        <div class="btn zero">0</div>
        <div class="btn">*</div>
        <div class="operator btn">=</div>

    </div>
</template>

<script>
export default{
    name: 'Calculator'
}

</script>
<style scoped>
.calculator{
    width: 30%;
    margin: auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
}
.display{
    padding:2rem;
    grid-column: 1/5;
    color: white;
    background: darkblue;
}
.zero{
    grid-column: 1/3;
}
.btn{
    padding: 1rem;
    background-color: #f2f2f2;
    border: 1px solid #333;
}
.operator{
    background-color: orange;
    color: white;
}

</style>