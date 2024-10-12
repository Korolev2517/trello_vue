<script>
import draggable from "vuedraggable";
import { ref } from "vue";

export default {
  components: {
    draggable,
  },
  setup() {
    const cards = ref([{ id: 0, title: '' }]);
    let id = 1;

    const createCard = () => {
      cards.value.push({ id: id++, title: `Card ${id}` });
    }

    return {
      cards,
      createCard
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="start-area">
      <div class="create_card" @click="createCard">+</div>
      <draggable
          class="cards"
          v-model="cards"
          group="people"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element }">
          <div class="card">
            {{ element.title }}
          </div>
        </template>
      </draggable>
    </div>
    <div class="card_area"></div>
    <div class="card_area"></div>
    <div class="card_area"></div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  width: 100vw;
  height: 100vh;
}
.start-area,
.card_area {
  margin: 1px;
  width: 25vw;
  height: 100%;
  border-radius: 7px;
  background-color: #f1eff2;
  text-align: center;
}
.create_card {
  display: flex;
  width: 40px;
  height: 40px;
  background-color: lightseagreen;
  border-radius: 7px;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 20px;
}
.cards {
  display: flex;
  flex-direction: column;
}
.card {
  width: 99%;
  height:70px;
  background-color: #2c3e50;
  color: white;
  margin: 5px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
}
</style>
