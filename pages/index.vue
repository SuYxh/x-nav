<script setup lang="ts">
import homeImg from "~/assets/images/home.jpg";
import { useRouter } from 'vue-router';

definePageMeta({
  layout: false,
});

const isLoading = ref(true)
const router = useRouter();

router.push('/tools'); // 在图片加载完成后重定向

onMounted(() => {
  const bg = new Image()
  bg.src = homeImg
  bg.onload =() => {
    isLoading.value = false
  }
  bg.onerror =() => {
    isLoading.value = false
  }
  setTimeout(() => {
    isLoading.value = false
  }, 2000);
})

</script>

<template>
  <div class="load-box" v-if="isLoading">
    <loading/>
  </div>
  
  <div class="page" v-else>
    <img src="~/assets/images/home.jpg" class="bg" alt="">
    <img src="~/assets/images/logo-text.png" alt="前端助手" class="img-title">
    <NuxtLink class="enter" to="/tools">进入</NuxtLink>
  </div>
</template>

<style lang="scss" scoped>
.load-box{
  background: #639;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.page{
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .bg{
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .img-title{
    height: 130px;
  }
  h1{
    font-size: 40px;
  }
  .enter{
    color: #fff;
    font-size: 20px;
    margin-top: 30px;
  }
}


.enter {
  --b: 3px;
   /* border thickness */
  --s: .45em;
 /* size of the corner */
  --color: #e2e2e2;
  font-weight: bold;
  padding: calc(.5em + var(--s)) calc(.9em + var(--s));
  color: var(--color);
  --_p: var(--s);
  background: conic-gradient(from 90deg at var(--b) var(--b),#0000 90deg,var(--color) 0)
    var(--_p) var(--_p)/calc(100% - var(--b) - 2*var(--_p)) calc(100% - var(--b) - 2*var(--_p));
  transition: .3s linear, color 0s, background-color 0s;
  outline: var(--b) solid #0000;
  outline-offset: .6em;
  font-size: 16px;
  border: 0;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.enter:hover,
.enter:focus-visible {
  --_p: 0px;
  outline-color: #ffffff;
  outline-offset: .05em;
}

.enter:active {
  background: #ffffff;
  color: #000000;
}

@media (max-width: 480px) {
  .page{
    .img-title{
      max-width: 80vw;
      height: 26vw;
    }
    .enter{
      font-size: 16px;
    }
  }
}
</style>