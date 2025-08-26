<script setup>

function goTo1() {
  window.location.href = "https://kimmh74.github.io/vue_day01_0822/";
}
function goTo2() {
  window.location.href = "https://kimmh74.github.io/vue_day02_0825/";
}
function goTo3() {
  window.location.href = "https://kimmh74.github.io/vue_day03_0826/";
}

</script>

<template>
  <div class="container">
    <h1 class="note-title">나만의 멋진 Vue_STUDY 노트<span>
        <p>st.kimmh</p>
      </span></h1>
    <div class="button-list">
      <button @click="goTo1" class="note-button">첫번날 : day01_0822</button>
      <button @click="goTo2" class="note-button">두번날 : day02_0825</button>
      <button @click="goTo3" class="note-button">세째날 : day03_0825</button>      
    </div>
  </div>

  <!-- <button @click="goToNaver">네이버로 이동</button> -->

</template>

<style scoped>
.container {
  width: 500px;
  margin: 30px auto;
  padding: 10px;
  background: #fffceb;
  border-radius: 16px;
  box-shadow: 4px 6px 12px rgba(251, 176, 45, 0.4);
  font-family: 'Nanum Gothic', sans-serif;
}

/* 제목 스타일 */
.note-title {
  font-size: 1.8em;
  font-weight: 700;
  color: #f9a825;
  /* 황금빛 느낌 */
  text-align: center;
  margin-bottom: 20px;
  padding: 10px 0;
  border-bottom: 3px dashed #fbc02d;
  text-shadow: 1px 1px 2px rgba(246, 190, 0, 0.6);
  user-select: none;
}

/* 버튼목록 세로 정렬 + 간격 */
.button-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.note-button:hover {
  background-color: #fff176;
  box-shadow: 4px 8px 12px rgba(0, 0, 0, 0.25);
}
</style>
