<script>
import draggable from "vuedraggable";
import { ref } from "vue";

export default {
  components: {
    draggable,
  },
  setup() {
    const cards = ref([{ id: Date.now(), title: '' }]);
    const cards1 = ref([{}]);
    const cards2 = ref([{}]);
    // let id = Date.now();

    const createCard = () => {
      cards.value.push({ id: Date.now(), title: `` });
    }

    return {
      createCard,
      cards,
      cards1,
      cards2
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
          :list="cards"
          group="task"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element }">
          <div class="card">
            {{ element.id }}
          </div>
        </template>
      </draggable>
    </div>
    <div class="card_area">Start
      <draggable

          :list="cards1"
          group="task"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element }">
          <div>
          </div>
        </template>
      </draggable>
    </div>
    <div class="card_area" draggable="true">In progress</div>
    <div class="card_area">Done</div>
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
