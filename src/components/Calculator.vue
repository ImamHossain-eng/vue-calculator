<template>
    <div class="calculator">
        <div class="display">{{current || '0'}}</div>
        <div @click="clear" class="btn">AC</div>
        <div @click="sign" class="btn">+/-</div>
        <div @click="percent" class="btn">%</div>
        <div @click="divide" class="operator btn">/</div>
        <div @click="append('7')" class="btn">7</div>
        <div @click="append('8')" class="btn">8</div>
        <div @click="append('9')" class="btn">9</div>
        <div @click="times" class="operator btn">x</div>
        <div @click="append('4')" class="btn">4</div>
        <div @click="append('5')" class="btn">5</div>
        <div @click="append('6')" class="btn">6</div>
        <div @click="minus" class="operator btn">-</div>
        <div @click="append('1')" class="btn">1</div>
        <div @click="append('2')" class="btn">2</div>
        <div @click="append('3')" class="btn">3</div>
        <div @click="add" class="operator btn">+</div>
        <div @click="append('0')" class="btn zero">0</div>
        <div @click="dot" class="dot btn"><b>.</b></div>
        <div @click="equal" class="operator btn">=</div>

    </div>
</template>

<script>
export default{
    name: 'Calculator',
    data() {
        return {
            previous: null,
            current: '',
            operator: null,
            operatorClicked: false,
        }
    },
    methods: {
        clear() {
            this.current='';
        },
        sign() {
            this.corrent = this.current.charAt(0) === '-' ?
            this.current.slice(1) : `-${this.current}`;
        },
        percent() {
            this.current = `${parseFloat(this.current) / 100}`;
        },
        append(number) {
            if (this.operatorClicked) {
                this.current = '';
                this.operatorClicked = false;
            }
            this.current = `${this.current}${number}`
        },
        dot() {
            if (this.current.indexOf('.') === -1) {
                this.append('.');
            }
        },
        setPrevious() {
            this.previous = this.current;
            this.operatorClicked = true;
        },
        divide() { 
            this.operator = (b, a) => a/b;
            this.setPrevious();
        },
        times() {
            this.operator = (a, b) => a*b;
            this.setPrevious();
        },
        minus() {
            this.operator = (b, a) => a-b;
            this.setPrevious();
        },
        add() {
            this.operator = (a, b) => a+b;
            this.setPrevious();             
        },
        equal() {
            this.current = `${this.operator(
                parseFloat(this.current),
                parseFloat(this.previous)
            )}`;
            this.previous = null;
        }
    }
}

</script>
<style scoped>
.calculator{
    margin-top: 20px;
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
    background: #212121;
}
.zero{
    grid-column: 1/3;
}
.btn{
    padding: 2rem 1rem;
    cursor: pointer;
    background-color: #f2f2f2;
    border: 1px solid #333;
}
.btn:hover{
    transition: .5s;
    transform: scale(1.1);
}
.operator{
    background-color: darkorange;
    color: white;
}
.dot{
    font-size: 2rem;
}

</style>