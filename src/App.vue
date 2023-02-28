<script setup>
import { computed, ref } from "vue";
import sourceImg from "./assets/source.png";
import dayjs from "dayjs";

const isThisMonth = ref(true)
function onChange(e) { isThisMonth.value = e.target.checked }

const refDate = computed(() => dayjs().subtract(isThisMonth.value ? 0 : 1, "month"));
const startOfMonth = computed(() => refDate.value.startOf("month").format("YYYY年MM月DD日"));
const endOfMonth = computed(() => refDate.value.endOf("month").format("YYYY年MM月DD日"));
const month = computed(() => String(refDate.value.month() + 1).padStart(2, "0"));
const year = computed(() => refDate.value.year());
</script>

<template>
  <img :src="sourceImg" class="source-img" />
  <div class="account1">159</div>
  <div class="account2">159</div>
  <div class="date1">{{ startOfMonth }}-{{ endOfMonth }}</div>
  <div class="date2">{{ month }}</div>
  <div class="date3">{{ year }}</div>
  <input type="checkbox" :checked="isThisMonth" @change="onChange" class="checkbox">
</template>

<style scoped>
.source-img {
  width: 100%;
  overflow: hidden;
}

.account1 {
  position: absolute;
  left: 533px;
  top: 371px;
  color: #fff;
  font-size: 36px;
  filter: blur(0.4px);
  background: url("./assets/background1.jpg") -170px -143px;
}

.account2 {
  position: absolute;
  left: 911px;
  top: 371px;
  color: #fff;
  font-size: 36px;
  filter: blur(0.4px);
  background: url("./assets/background1.jpg") -515px -132px;
}

.date1 {
  position: absolute;
  left: 875px;
  top: 104px;
  color: #4156c4;
  font-size: 18px;
  filter: blur(0.4px);
  background: url("./assets/background2.jpg") -515px -30px;
}

.date2 {
  position: absolute;
  left: 940px;
  top: 498px;
  color: #3d4245;
  font-size: 20px;
  filter: blur(0.4px);
  background: #fff;
}

.date3 {
  position: absolute;
  left: 647px;
  top: 556px;
  color: #3d4245;
  font-size: 22px;
  filter: blur(0.5px);
  background: #fff;
}

.checkbox {
  display: none;
}
</style>
