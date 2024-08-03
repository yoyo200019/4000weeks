<script setup lang="ts">
import { ref } from "vue";

const count = ref(0);
const inputValue = ref("1995-05-30");

const getWeeks = (born = "1995-05-30") => {
  const now = new Date();
  const specificDate = new Date(born);
  const difference = now.getTime() - specificDate.getTime();
  // 將毫秒轉成天數，再轉成週數
  const daysDifference = parseInt(
    parseInt(difference / (1000 * 60 * 60 * 24)) / 7,
  );

  // count.value = daysDifference;

  count.value = 54 * 42;
};
getWeeks();
</script>

<template>
  <div>
    <h3>人生的4000個禮拜</h3>
    <ul>
      <li>
        <label for="dateInput">生日：</label>
        <input
          type="date"
          id="dateInput"
          name="dateInput"
          v-model="inputValue"
          @input="getWeeks(inputValue)"
        />
      </li>
      <li>從出生到現在已經過了 {{ count }} 週</li>
      <li>從出生到現在已經過了 {{ (count / 4000) * 100 }} %</li>
    </ul>
    <div class="firstBox">
      <div class="firstBox2">
        <template v-for="i in 4000" :key="i">
          <div
            :class="{
              sub: true,
              firstBoxSub: true,
              // yes: count > i,
              yes: 4000 - count < i,
              //  (4000 - count)

              // red: i === 100,
            }"
          ></div>
        </template>
      </div>
    </div>
    <div class="outBox">
      <div class="box">
        <template v-for="i in 4000" :key="i">
          <div
            :class="{
              sub: true,
              // yes: count > i,
              yes: 4000 - count < i,
              //  (4000 - count)

              // red: i === 100,
            }"
          ></div>
        </template>
      </div>
    </div>
  </div>
</template>

<style scoped>
div {
  box-sizing: border-box;
}
.firstBox {
  width: 510px;
  /* height: 510px; */
  border: 5px solid #598987;
  margin-bottom: 12.5px;
}
.firstBox2 {
  width: 510px;
  height: 510px;
  /* width: 440px; */
  display: flex;
  flex-wrap: wrap;
  /* border-radius: 20px; */
  overflow: hidden;
}
.firstBox2 .firstBoxSub {
  width: 5px;
  height: 12.5px;
  /* height: 10px; */
  border: 0.3px solid rgba(128, 128, 128, 0.5);
}
.outBox {
  width: 510px;
  height: 510px;
  /* background-image: url("https://picsum.photos/300/300?image=1056"); */
  background-image: url("https://i.imgur.com/sIdzCgc.png");
  background-image: url("https://pbs.twimg.com/media/F9XYN41boAAyHG3?format=jpg&name=large");
  /* background-image: url("https://pbs.twimg.com/profile_images/1712203252065050624/_7ZyJcHu_400x400.jpg"); */

  background-size: 100% 100%; /* 背景图片的大小，与容器大小相同 */
  background-repeat: no-repeat; /* 禁止背景图片重复 */
  background-size: cover;
  border-radius: 50%;
}

.box {
  border: 5px solid #598987;
  width: 510px;
  height: 510px;
  /* width: 440px; */
  display: flex;
  flex-wrap: wrap;
  /* border-radius: 20px; */
  border-radius: 50%;
  overflow: hidden;
}
.box .sub {
  width: 5px;
  height: 12.5px;
  /* height: 10px; */
  /* border: 0.3px solid rgba(128, 128, 128, 0.5); */
}

.yes {
  /* background-color: rgba(255, 0, 0, 0.5); */
  background-color: rgba(128, 128, 128, 0.3);
  /* border: 0.3px solid rgba(128, 128, 128, 0); */
  /* border: 0.3px solid blue; */
}
.red {
  background-color: red;
}
/* input[type="date"]::-webkit-calendar-picker-indicator {
  display: none;
} */
</style>
