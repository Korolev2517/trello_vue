<script setup>
import { ref } from "vue";

const cards = ref([]);
const emit = defineEmits(['onDrop'])


function createCard() {
  cards.value.push({ id: Date.now(), content: "" });
}

const dragStart = (event, card) => {
  event.dataTransfer.dropEffect = 'move';
  event.dataTransfer.effectAllowed = 'move';
  event.dataTransfer.setData('cardId', card.id);
  console.log('drag')
}

const onDrop = (event, area) => {
  const cardId = event.dataTransfer.getData('cardId');
  const card = cards.value.find((card) => cards.id === cardId);
  card.area = area;
}

</script>

<template>
  <div class="btn" @click="createCard">+</div>
  <div v-for="card in cards"
       :key="card.id"
       class="card"
       draggable="true"
       @dragstart="dragStart($event, card)">
    {{ card.content }}
  </div>
</template>

<style scoped>
.btn {
  display: flex;
  margin-left: 10px;
  margin-top: 10px;
  width: 50px;
  height: 50px;
  border-radius: 7px;
  font-size: 35px;
  font-weight: bold;
  justify-content: center;
  align-items: center;
  background-color: lightgreen;
}
.card {
  margin: 8px 2px;
  width: 98%;
  height: 100px;
  background-color: lightgreen;
  border-radius: 7px;
}
</style>

