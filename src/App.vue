<script setup>
import CreateBtn from "@/components/CreateBtn.vue";
import CardArea from "@/components/CardArea.vue";

</script>

<template>
<div class="container" >
  <div class="start_area"><CreateBtn /></div>
  <CardArea><p>Start</p></CardArea>
  <CardArea><p>In progress</p></CardArea>
  <CardArea><p>Done</p></CardArea>
</div>
</template>

<style scoped>
.container {
  display: flex;
  width: 100vw;
  height: 100vh;
}
.start_area {
  margin: 1px;
  width: 25vw;
  height: 100%;
  border-radius: 7px;
  background-color: #f1eff2;
  text-align: center;
}
</style>
