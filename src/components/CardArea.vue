<script setup>
import CreateBtn from "@/components/CreateBtn.vue";

</script>

<template>
  <div class="card_area" @dragover.prevent><slot/></div>
</template>

<style scoped>
.card_area {
  margin: 1px;
  width: 25vw;
  height: 100%;
  border-radius: 7px;
  background-color: #f1eff2;
  text-align: center;
}
</style>