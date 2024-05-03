<template>
  <div class="page">
    <img src="https://qn.huat.xyz/mac/202404160043547.png" alt="" />
    <img src="https://qn.huat.xyz/mac/202404160040430.png" alt="" />
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.page {
  display: flex;
  column-gap: 100px;
  justify-content: center;
  align-items: center;
  img {
    display: block;
    width: 40vw;
    max-width: 40vw;
    height: 70vh;
    object-fit: cover;
  }
}

@media (max-width: 480px) {
  .page {
    flex-direction: column;
    img {
      height: 90vh;
    }
  }
}
</style>
