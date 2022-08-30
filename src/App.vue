
<script setup>
import Maindoor from './components/Maindoor.vue';
import Greeting from './components/Greeting.vue';
import Gallery from './components/Gallery.vue';
</script>

<template>
  <div style="text-align: center;margin-left:auto;margin-right:auto;">
    <Maindoor />
  </div>
  <div style="text-align: center;margin-left:auto;margin-right:auto;">
    <Greeting />
  </div>
  <div style="text-align: center;margin-left:auto;margin-right:auto;width:75%">
    <Gallery />
  </div>
  <div style="text-align: center;margin-left:auto;margin-right:auto;width:75%">
    연락처 및 계좌
  </div>
  <div style="text-align: center;margin-left:auto;margin-right:auto;width:75%"  >
    댓글
  </div>
</template>

