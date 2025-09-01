<template>
    <div class="temp-bg">
        <button v-on:click="cnt++">++1 증가버튼 [{{ cnt }}]</button>
        <hr>
        <!-- //전구불 ON/OFF  -->
        <img :src="lightOn ? pic_bulbon : pic_bulboff" alt="pic_bulboff">
        <button @click="lightOn = !lightOn">ON/OFF 버튼{{ lightOn }}</button>
        <hr>
        <!-- // 키입력 -->
        <div>
            <input type="text " @input="inputCount++">
            <p>{{ inputCount }}번째키를 누르고 있음(지움포함)</p>
        </div>
        <hr>
        <!-- // 색상 값 -->
        <div class="bg" @mousemove="colorVal = Math.floor(Math.random() * 360)"
            :style="{ backgroundColor: `hsl(${colorVal},60%,60%)` }">
            {{ colorVal }}
        </div>

        <!-- //메뉴판 -->
        <div class="menu">
            <ol>
                <li v-for="food in foods_assets" @click="imgUrl = food.src">
                    {{ food.name }}
                </li>
            </ol>
            <img :src="imgUrl" alt="food.name">
        </div>
        <p class="enter"></p>
        <hr>
    </div>

</template>

<script setup>
import { ref } from 'vue';

import pic_bulboff from '../assets/pic_bulboff.gif'
import pic_bulbon from '../assets/pic_bulbon.gif'

import img_burrito from '../assets/img_burrito.svg'
import img_salad from '../assets/img_salad.svg'
import img_cake from '../assets/img_cake.svg'
import img_soup from '../assets/img_soup.svg'
import img_fish from '../assets/img_fish.svg'
import img_pizza from '../assets/img_pizza.svg'
import img_rice from '../assets/img_rice.svg'





const cnt = ref(0)
//전구불을 켜고끄는 토글버튼 ==> lightOn이 img경로에 확인하여 붙임.
const lightOn = ref(true)

//키입력시에 카운트를 증가
const inputCount = ref(0)

//색상값
const colorVal = ref(50)

//메뉴판
const foods_assets = ref([
    { name: '브리또', src: img_burrito },
    { name: '샐러드', src: img_salad },
    { name: '케이크', src: img_cake },
    { name: 'Soup', src: img_soup },
    { name: '생선', src: img_fish },
    { name: '피자', src: img_pizza },
    { name: '밥', src: img_rice },
])

const imgUrl = ref(img_burrito)

</script>

<style scoped>
.temp-bg {
    height: 100%;

}

.bg {
    width: 200px;
    height: 50px;
    background-color: aquamarine;
    display: inline-block;
}

.menu>ol {
    width: 150px;
    float: left;
}

.menu li:hover {
    cursor: pointer;
    background-color: rgb(219, 74, 17);
}

.menu>img {
    width: 200px;
    height: 200px;
}

.enter {
    clear: both
}
</style>