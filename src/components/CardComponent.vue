<script>
export default {
  props: {
    card: Object,
  },
  methods: {
    updateCardTitle(card, newTitle) {
      this.$emit('update-title', card, newTitle);
    },
  },
};
</script>

<template>
  <div class="card_container">
    <div class="card">
    <textarea
        type="text"
        v-model="card.title"
        placeholder="Enter text"
        @input="updateCardTitle(card, card.title)"
    />
    </div>
  </div>
</template>

<style scoped>
.card_container {
  display: flex;
  justify-content: center;
  margin: 3px 4px;
}

.card {
  width: 100%;
  height: 70px;
  margin: 0;
  padding: 0;
  display: flex;
  color: #181818;
  align-items: center;
  justify-content: center;
  border: 1px solid lightgreen;
  border-radius: 4px;
}
</style>
