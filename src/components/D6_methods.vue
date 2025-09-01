<template>
    <div class="bg">
        <div class="b1" @click="changText">
            <p>{{ text }}</p>
        </div>


    </div>
    <div class="bg">
        <div class="b2" @mousemove="mousePos">
            <span>xPos{{ xPos }}----yPos{{ yPos }}</span>
        </div>

    </div>
    <div class="bg">
        <div class="bg3">
            <p class="count-box"> {{ count }} </p><br></br>
            <button @click="addCount(1)">++1 증가</button><br>
            <button @click="addCount(5)">++5 증가</button><br>
            <button @click="addCount(-1)">--1 감소</button><br>
            <button @click="addCount(-3)">--3 감소</button><br>
        </div>
    </div>
    <div class="bg">
        <div class="b4">
            <img id="tiger" @click="myMethod($event, '안녕~')" :src="img_tiger_square" alt="타이거사진">
            <p>{{ msgAndId }}</p>

        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue';
import img_tiger_square from '../assets/images/img_tiger_square.jpeg'

const text = ref('눌러')
// const changText = () => {} - 요즘 함수로 많이 사용 같은 함수.
function changText() {
    text.value = '안녕 ~'
}
// X좌표 Y좌표 표시........width와 height값을 200px안에서 변경px변환 확인
const xPos = ref(0)
const yPos = ref(0)
//e이벤트 변수를 넣어주면 쓸수 있음.
const mousePos = (e) => {
    xPos.value = e.offsetX
    yPos.value = e.offsetY
}

//----
const count = ref(0)
//메소드... 증가하는
const addCount = (num) => {
    count.value += num
}

//----

const msgAndId = ref('')
//myMethod($event,'안녕~')
const myMethod = (e, msg) => {
    // msgAndId.value = msg
    // msgAndId.value += e.target.id
    msgAndId.value = `${e.target.id}야 ${msg} 좋은하루!!!`
}

</script>

<style scoped>
.bg {
    margin: 10px;
    border-bottom: 3px double purple;
}

.b1 {
    width: 200px;
    height: 100px;
    background-color: rgb(231, 79, 14);
    display: inline-block;
}

.b2 {
    width: 200px;
    height: 200px;
    background-color: rgb(195, 208, 19);
    display: inline-block;
}

.b3 {
    background-color: rgb(195, 208, 19);
    display: inline-block;

}

button {
    background-color: greenyellow;
    margin: 5px;
    border: 1px dotted red;
}

.b4>img {
    width: 200px;
    height: 200px;
}

.count-box {
    display: inline-block;
    border: 3px solid #333;
    padding: 5px 10px;
    border-radius: 50px;
    min-width: 50px;
    text-align: center;
    user-select: none;
}
</style>