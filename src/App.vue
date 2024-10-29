<script>
import ColumnComponent from 'components/ColumnComponent.vue';
import CardComponent from 'components/CardComponent.vue';
import ModalComp from "components/ModalComp.vue";
import draggable from "vuedraggable";
import { ref } from 'vue';

export default {
  components: {
    ColumnComponent,
    CardComponent,
    ModalComp,
    draggable
  },
  setup() {
    const cards = ref([]);
    const cards1 = ref([]);
    const cards2 = ref([]);
    const cards3 = ref([]);
    const showModal = ref(false)

    const createCard = () => {
      showModal.value = true;
    };

    const addCard = (cardData) => {
      cards.value.push({
        id: Date.now(),
        title: cardData.title,
        text: cardData.cardText,
        note: cardData.note
      });
      showModal.value = false;
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
      updateCardTitle,
      showModal,
      addCard
    };
  },
};
</script>

<template>
  <div class="container">
    <div class="start-area">
      <div class="create_card" @click="createCard">+</div>
      <Teleport to="body">
        <ModalComp :show="showModal" @close="showModal = false" @save="addCard">
        </ModalComp>
      </Teleport>
      <draggable
          class="cards"
          :list="cards"
          group="task"
          @start="drag = true"
          @end="drag = false"
          item-key="id"
      >
        <template #item="{ element: card }">
          <CardComponent :card="card" @update-title="updateCardTitle" />
        </template>
      </draggable>
    </div>

    <ColumnComponent
        title="Start"
        :cards="cards1"
        @update-title="updateCardTitle"
    />
    <ColumnComponent
        title="In Progress"
        :cards="cards2"
        @update-title="updateCardTitle"
    />
    <ColumnComponent
        title="Done"
        :cards="cards3"
        @update-title="updateCardTitle"
    />
  </div>
</template>


<style scoped>
.container {
  display: flex;
  width: 100vw;
  min-height: 100vh;
  box-sizing: border-box;
  padding: 10px;
}

.start-area {
  display: flex;
  flex-direction: column;
  margin-right: 1px;
  width: 25vw;
  min-height: 100vh;
  border-radius: 7px;
  background-color: #f1eff2;
}

.create_card {
  display: flex;
  margin: 10px;
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
</style>
