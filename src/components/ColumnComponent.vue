<script>
import CardComponent from './CardComponent.vue';
import draggable from "vuedraggable";

export default {
  components: {
    CardComponent,
    draggable
  },
  props: {
    title: String,
    cards: Array,
  },
  methods: {
    updateCardTitle(card, newTitle) {
      card.title = newTitle;
    },
  },
};
</script>

<template>
  <div class="card_area">
    <div class="title">
      <h4>{{ title }}</h4>
    </div>
    <div class="drop_area">
      <draggable
          class="cards"
          :list="cards"
          group="task"
          @start="drag = true"
          @end="drag = false"
          item-key="id"
      >
        <template #item="{ element: card }">
          <CardComponent
              :card="card"
              @update-card="$emit('update-card', card)"
          />
        </template>
      </draggable>
    </div>
  </div>
</template>



<style scoped>
.card_area {
  display: flex;
  flex-direction: column;
  margin-right: 1px;
  box-sizing: border-box;
  width: 25vw;
  min-height: 300px;
  border-radius: 7px;
  background-color: #f1eff2;
}

.title {
  display: flex;
  width: 100%;
  height: 60px;
  text-align: center;
  align-items: center;
}

h4 {
  margin: 0 auto;
  align-items: center;
}

.drop_area {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  min-height: 400px;
  box-sizing: border-box;
}

.cards {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
}
</style>
