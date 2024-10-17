<script>
import draggable from "vuedraggable";
import { ref } from "vue";

export default {
  components: {
    draggable,
  },
  setup() {
    const cards = ref([]);
    const cards1 = ref([]);
    const cards2 = ref([]);
    const cards3 = ref([]);

    const createCard = () => {
      cards.value.push({ id: Date.now(), title: '' });
    };

    const updateCardTitle = (card, newTitle) => {
      card.title = newTitle;
    };

    return {
      createCard,
      cards,
      cards1,
      cards2,
      cards3,
      updateCardTitle
    };
  },
};
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
        <template #item="{ element: card }">
          <div class="card">
            <input
                type="text"
                v-model="card.title"
                placeholder="Enter text"
                @input="updateCardTitle(card, card.title)"
            />
          </div>
        </template>
      </draggable>
    </div>

    <div class="card_area">
      <h4>Start</h4>
      <draggable
          class="cards"
          :list="cards1"
          group="task"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element: card }">
          <div class="card">
            <input
                type="text"
                v-model="card.title"
                placeholder="Enter text"
                @input="updateCardTitle(card, card.title)"
            />
          </div>
        </template>
      </draggable>
    </div>

    <div class="card_area">
      <h4>In progress</h4>
      <draggable
          class="cards"
          :list="cards2"
          group="task"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element: card }">
          <div class="card">
            <input
                type="text"
                v-model="card.title"
                placeholder="Enter text"
                @input="updateCardTitle(card, card.title)"
            />
          </div>
        </template>
      </draggable>
    </div>

    <div class="card_area">
      <h4>Done</h4>
      <draggable
          class="cards"
          :list="cards3"
          group="task"
          @start="drag=true"
          @end="drag=false"
          item-key="id">
        <template #item="{ element: card }">
          <div class="card">
            <input
                type="text"
                v-model="card.title"
                placeholder="Enter text"
                @input="updateCardTitle(card, card.title)"
            />
          </div>
        </template>
      </draggable>
    </div>
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
  margin: 2px 2px;
  width: 40px;
  height: 40px;
  background-color: lightseagreen;
  border-radius: 7px;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 20px;
  cursor: pointer;
}
.cards {
  display: flex;
  flex-direction: column;
  height: 100%;
}
h4 {
  margin: 13px;
}
.card {
  width: 99%;
  height: 70px;
  margin: 3px 3px;
  padding: 0;
  display: flex;
  color: #181818;
  align-items: center;
  justify-content: center;
  border: 1px solid lightgreen;
  border-radius: 4px;
}
.card input {
  width: 90%;
  height: 30px;
  border: none;
  text-align: center;
  font-size: 16px;
  border-radius: 4px;
  outline: none;
}
</style>
