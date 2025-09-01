<template>
    <div>
        <label>
            <input @change="handleChang" v-model="selected" type="radio" id="R-1" value="HTML" name="radioG" />HTML
        </label>
        <label>
            <input @change="handleChang" v-model="selected" type="radio" id="R-2" value="CSS" name="radioG" />CSS
        </label>
        <label>
            <input @change="handleChang" v-model="selected" type="radio" id="R-3" value="JS" name="radioG" />JS
        </label>
        <label>
            <input @change="handleChang" v-model="selected" type="radio" id="R-4" value="React" name="radioG" />REACT
        </label>
        <label>
            <input @change="handleChang" v-model="selected" type="radio" id="R-5" value="Vue" name="radioG" />VUE
        </label>
        <p>선택 값 : {{ selected }}</p>
        <p>선택 ID값 : {{ selectedID }}</p>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const selected = ref('HTML')
const selectedID = ref('')

const handleChang = (e) => {
    selectedID.value = e.target.id
}
</script>

<style scoped></style>