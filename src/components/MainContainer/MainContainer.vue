<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';
const currentTime = ref('');
const timerDiscourse = ref('欢迎您来到喵羽乐园Naigos奶果站！~');
function updateTime() {
  const date = new Date();
  const hours = date.getHours().toString().padStart(2, '0');
  const minutes = date.getMinutes().toString().padStart(2, '0');
  currentTime.value = `${hours}:${minutes}`;
  if (0 <= date.getHours() && date.getHours() <= 1){
    timerDiscourse.value = '午夜了，要注意休息！';
  } else if (2 <= date.getHours() && date.getHours() <= 4){
    timerDiscourse.value = '已经是深夜了喔，还要来看看奶果站吗？';
  } else if (5 <= date.getHours() && date.getHours() <= 7){
    timerDiscourse.value = '一日之计在于晨，欢迎访问奶果站！';
  } else if (8 <= date.getHours() && date.getHours() <= 11){
    timerDiscourse.value = '上午好！愿夜战家奶果~喵羽乐园能一直为您带来快乐！';
  } else if (12 <= date.getHours() && date.getHours() <= 13){
    timerDiscourse.value = '要按时吃午饭哦！';
  } else if (14 <= date.getHours() && date.getHours() <= 18){
    timerDiscourse.value = '下午好！有记得为奶果档案签到吗？';
  } else if (19 <= date.getHours() && date.getHours() <= 20){
    timerDiscourse.value = '傍晚的惬意，是否让您感到放松？~';
  } else if (21 <= date.getHours() && date.getHours() <= 23){
    timerDiscourse.value = '夜晚，是最令人放空自我，安心的时间，是吗？';
  } else {
    timerDiscourse.value = '欢迎您来到喵羽乐园Naigos奶果站！~'
  }
}
onMounted(() => {
  const timer = setInterval(updateTime, 1000);
  const hours = new Date().getHours();
  if (0 <= hours && hours <= 3)
    onBeforeUnmount(() => {
      clearInterval(timer);
    });
});
</script>

<template>
  <div class="main_container_box">
    <div class="header_timer" style="height: 140px">
      <p>{{currentTime}}&nbsp;&nbsp;&nbsp;{{timerDiscourse}}</p>
    </div>
    <div class="functional_box">
      <div class="function_item"><a href="#notice_anchor"><img src="@/assets/MainView/Functional/notice.jpg" alt="notice"/></a></div>
      <div class="function_item"><a href="#"><img src="@/assets/MainView/Functional/naigos_bot.jpg" alt="naigosbot"/></a></div>
      <div class="function_item"><a href="#"><img src="@/assets/MainView/Functional/sarchive_service.jpg" alt="naigosbot"/></a></div>
      <div class="function_item"><a href="#"><img src="@/assets/MainView/Functional/games.jpg" alt="naigosbot"/></a></div>
      <div class="function_item"><a target="_blank" href="https://yasenbaka.work"><img src="@/assets/MainView/Functional/blog.jpg" alt="naigosbot"/></a></div>
      <div class="function_item"><a href="#"><img src="@/assets/MainView/Functional/naigos_miaoyu.jpg" alt="naigosbot"/></a></div>
      <div class="function_item"><a target="_blank" href="https://www.yasenbaka.work/terms-of-service/"><img src="@/assets/MainView/Functional/service_agreement_privacy_terms.jpg" alt="naigosbot"/></a></div>
    </div>
    <div class="banner">
      banner
    </div>
    <div class="works_details_container_box">
      <div class="works_box">作品区</div>
      <div class="details_box">日志区</div>
    </div>
    <div class="notice_box">
      <a id="notice_anchor"/>
      <div class="notice_item">公告内容框</div>
    </div>
  </div>

</template>

<style scoped lang="sass">
.main_container_box
  margin: 0 auto
  width: 75%
  .functional_box
    display: flex
    justify-content: space-between
  .function_item

    a
      img
        border-radius: 10px
        opacity: .8
        transition: .5s
        width: 150px
        height: 80px
      img:hover
        opacity: 1

  .banner
    margin: 30px auto
    height: 300px
    border: 1px solid black
    border-radius: 10px
  .works_details_container_box
    display: grid
    grid-template-columns: 65% 30%
    grid-gap: 5%
    height: 300px
    .works_box
      border: 1px solid black
      border-radius: 10px
    .details_box
      border: 1px solid black
      border-radius: 10px
  .notice_box
    border: 1px solid black
    margin: 30px auto
    border-radius: 10px
    height: 300px
  .header_timer
    position: relative
    p
      margin: 0
      position: absolute
      left: 50%
      bottom: 15%
      transform: translate(-50%)
</style>