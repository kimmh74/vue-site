<template>
    <div class="bg">
        <!-- //양방향 바인딩 -->
        <div class="b1">
            <input type="text" v-model="inpText">
            <p>{{ inpText }}</p>
        </div>
    </div>
    <div class="bg">
        <div class="b2">
            <p>중요한가요?
                <label>
                    <input type="checkbox" v-model="important">
                    {{ important }}
                </label>
            </p>
        </div>
    </div>
    <div class="bg">
        <div class="b3">
            <!-- shoppingList 입력담당 -->
            <form @submit.prevent="addItem">
                <p>구매목록?
                    <input type="text" v-model="itemName" placeholder="목록 이름을 입력하세요">
                </p>
                <p>
                    구매갯수?
                    <input type="number" v-model="itemNumber" placeholder="구매 갯수를 입력하세요.">
                </p>

                <p>
                    얼마나 중요한가요?
                    <label>
                        <input type="checkbox" v-model="itemImportant">
                        {{ itemImportant }}
                    </label>
                    <!-- //label -- false/true 누름 -->
                <h2><strong>=== 구매 목록===</strong></h2>
                </p>
                <button type="submit">목록 추가하기</button>
            </form>

            <hr>
            <!-- //shoppingList 출력담당 -->

            <ol>
                <li v-for="list in shoppingList">
                    목록 : {{ list.name }} -
                    갯수 : {{ list.number }} -
                    중요도 : {{ list.important }}
                </li>
            </ol>
        </div>
    </div>


</template>

<script setup>
import { ref } from 'vue';

// 양방향 바인딩
const inpText = ref('Initial text')
//
const important = ref(false)

//쇼핑목록.......
const itemName = ref(null)
const itemNumber = ref(null)
const itemImportant = ref(false)
const addItem = () => {
    let item = {
        name: itemName.value,
        number: itemNumber.value,
        important: itemImportant.value
    }
    shoppingList.value.push(item)

    //목록 init 초기화
    itemName.value = null
    itemNumber.value = null
    itemImportant.value = false
}

const shoppingList = ref(
    [
        { name: 'Tomatoes', number: 5, important: false },
        { name: '바나나', number: 10, important: true }


    ]
)

</script>

<style scoped>
.bg {
    margin: 10px;
    border-bottom: 3px double purple;
}

.b1 {
    width: 200;
    height: 300;
    background-color: yellow;
}

.b2 {
    width: 200px;
    height: 50px;
    background-color: rgb(195, 208, 19);
    display: inline-block;
}

.b3 {
    width: 400px;
    background-color: rgb(249, 211, 235);
    display: inline-block;
    border: 1px dotted red;

}

ol li {
    border-bottom: 1px solid white;
}
</style>