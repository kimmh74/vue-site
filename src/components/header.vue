<template>
  <div>
    <header>
      <h2>Vue 과제<br />Study List</h2>
      <nav>
        <ul class="main-menu">
          <li v-for="(menu, index) in menus" :key="index" class="menu-item" @mouseenter="hoverIndex = index"
            @mouseleave="hoverIndex = null">
            <a href="#">{{ menu.title }}</a>

            <!-- 서브 메뉴 -->
            <ul v-if="hoverIndex === index" class="submenu">
              <li v-for="(sub, subIndex) in menu.submenus" :key="subIndex">
                <a href="#" @click.prevent="openSlide(menu.title, sub)">{{ sub }}</a>
              </li>
            </ul>
          </li>
        </ul>
      </nav>
    </header>

    <section class="slide-content" :class="{ show: slideVisible }">
      <button class="close-btn" @click="closeSlide">✕ 닫기</button>
      <div class="slide-inner">
        <h3>{{ selectedMenu }}</h3>
        <p>{{ selectedSub }}</p>
        <component v-if="currentComponent" :is="currentComponent" />
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import MyHellow from './MyHellow.vue';
import HelloWorld from './HelloWorld.vue';
import D1_bind from './D1_bind.vue';
import D2_if from './D2_if.vue';
import D3_show from './D3_show.vue';
import D4_for from './D4_for.vue';
import D5_event from './D5_event.vue';
import D6_methods from './D6_methods.vue';
import D7_model from './D7_model.vue';
import D8_computed from './D8_computed.vue';
import D9_watch from './D9_watch.vue';
import D10_form from './D10_form.vue';
import D11_homeTest from './D11_homeTest.vue';


const hoverIndex = ref(null);
const slideVisible = ref(false);
const selectedMenu = ref('');
const selectedSub = ref('');
const currentComponent = ref(null);


const menus = ref([
  { title: 'Day01_0822', submenus: ['Vue와 첫만남', '기본Vue 숫자세기'] },
  { title: 'Day02_0825', submenus: ['1.v-bind', '2.v-if', '3.v-show'] },
  { title: 'Day03_0826', submenus: ['4.v-for', '5.v-event'] },
  { title: 'Day04_0827', submenus: ['6.v-methods', '7.v-model', '8.v-computed', '9.v-watch', '10.v-form','11.웹기능사 A-4 유진건설'] }
]);;

function openSlide(menu, sub) {
  selectedMenu.value = menu;
  selectedSub.value = sub;
  // Map submenu to component
  if (menu === 'Day01_0822' && sub === 'Vue와 첫만남') {
    currentComponent.value = MyHellow;
  } else if (menu === 'Day01_0822' && sub === '기본Vue 숫자세기') {
    currentComponent.value = HelloWorld;
  } else if (menu === 'Day02_0825' && sub === '1.v-bind') {
    currentComponent.value = D1_bind;
  } else if (menu === 'Day02_0825' && sub === '2.v-if') {
    currentComponent.value = D2_if;
  } else if (menu === 'Day02_0825' && sub === '3.v-show') {
    currentComponent.value = D3_show;
  } else if (menu === 'Day03_0826' && sub === '4.v-for') {
    currentComponent.value = D4_for;
  } else if (menu === 'Day03_0826' && sub === '5.v-event') {
    currentComponent.value = D5_event;
  } else if (menu === 'Day04_0827' && sub === '6.v-methods') {
    currentComponent.value = D6_methods;
  } else if (menu === 'Day04_0827' && sub === '7.v-model') {
    currentComponent.value = D7_model;
  } else if (menu === 'Day04_0827' && sub === '8.v-computed') {
    currentComponent.value = D8_computed;
  } else if (menu === 'Day04_0827' && sub === '9.v-watch') {
    currentComponent.value = D9_watch;
  } else if (menu === 'Day04_0827' && sub === '10.v-form') {
    currentComponent.value = D10_form;
  } else if (menu === 'Day04_0827' && sub === '11.웹기능사 A-4 유진건설') {
    currentComponent.value = D11_homeTest;
  } else {
    currentComponent.value = null;
  }
  slideVisible.value = true;
}



function closeSlide() {
  slideVisible.value = false;
}
</script>

<style scoped>
/* 고정된 왼쪽 메뉴 영역 */
header {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 200px;
  background-color: #e6cba4;
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-sizing: border-box;
  z-index: 1000;
}

header h2 {
  font-size: 30px;
  text-align: center;
  color: #3d155f;
  margin-bottom: 20px;
  white-space: pre-line;
  /* 줄바꿈 유지 */
}

.main-menu {
  list-style: none;
  padding: 10px;
  margin: 10px 0 0 10px;
  display: flex;
  flex-direction: column;
  width: 100%;
}

.menu-item {
  position: relative;
  margin: 10px;
}

.menu-item>a {
  color: white;
  text-decoration: none;
  padding: 12px;
  display: block;
  width: 100%;
  text-align: center;
  font-weight: bold;
  background-color: #3d155f;
  border-radius: 4px;
}

.menu-item:hover>a {
  background-color: #f96167;
}

/* .submenu{
    display: none;
} */
.submenu {
  position: absolute;
  top: 0;
  left: 110%;
  background: #444;
  list-style: none;
  padding: 3px 0;
  margin: 0;
  min-width: 160px;
  border-radius: 4px;
  z-index: 1000;
}

/* .submenu li a {
display: block;
    background: #fff;
    padding: 5px;
    text-align: center;
    font-size: 14px;
} */
.submenu li a {
  color: white;
  padding: 8px 15px;
  display: block;
  text-decoration: none;
  cursor: pointer;
}

.submenu li a:hover {
  background: red;
  color: green;
}

/* 오른쪽 슬라이드 결과 영역 */
.slide-content {
  position: fixed;
  top: 0;
  left: 200px;
  /* 왼쪽 메뉴 너비만큼 띄움 */
  width: calc(100% - 200px);
  background: #fff;
  box-shadow: -4px 0 10px rgba(0, 0, 0, 0.2);
  transform: translateX(100%);
  transition: transform 0.3s ease;
  display: flex;
  justify-content: center;
  /* 가로 중앙 */
  align-items: center;
  /* 세로 중앙 */
  flex-direction: column;
  padding: 20px;
  box-sizing: border-box;
  /* z-index: 1000; */
  overflow-y: auto;
  /* 세로 스크롤 활성화 */
  overflow-x: auto;
  /* 가로 스크롤 방지 */
  /* background-image: url('../assets/images/img_tiger_square.jpeg'); */
}

.slide-content.active {
  transform: translateX(0);
  /* active 클래스가 붙으면 제자리로 슬라이드 인 */
}

.slide-content.show {
  transform: translateX(0);
}

.slide-inner {
  max-width: 800px;
  width: 100%;
  text-align: center;
  color: #333;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 20px;
  background: transparent;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #777;
  transition: color 0.2s ease;
}

.close-btn:hover {
  color: #333;
}
</style>