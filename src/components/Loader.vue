<template>
  <div class="loading-box">
      <div class="ripple">
            <div></div>
            <div></div>
        </div>
  </div>
</template>

<script>
export default {
    
}
</script>

<style>
    .loading-box {
        margin-top: 80px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .ripple {
        display: inline-block;
        position: relative;
        width: 80px;
        height: 80px;
    }
    .ripple div {
        position: absolute;
        border: 4px solid #fff;
        opacity: 1;
        border-radius: 50%;
        animation: ripple 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
    }
    .ripple div:nth-child(2) {
        animation-delay: -0.5s;
    }
    @keyframes ripple {
        0% {
            top: 36px;
            left: 36px;
            width: 0;
            height: 0;
            opacity: 0;
        }
        4.9% {
            top: 36px;
            left: 36px;
            width: 0;
            height: 0;
            opacity: 0;
        }
        5% {
            top: 36px;
            left: 36px;
            width: 0;
            height: 0;
            opacity: 1;
        }
        100% {
            top: 0px;
            left: 0px;
            width: 72px;
            height: 72px;
            opacity: 0;
        }
    }
</style>