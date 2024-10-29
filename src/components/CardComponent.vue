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
      <img src="../assets/img/edit.png" class="img" alt="#">
      <div class="card-content">
        <h3>{{ card.title }}</h3>
        <p>{{ card.text }}</p>
        <small>{{ card.note }}</small>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card_container {
  margin: 0 4px;
  width: 100%;
}

.card {
  display: flex;
  margin: 2px 4px;
  width: 85%;
  padding: 10px;
  background-color: #fff;
  border: 1px solid lightgreen;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  flex-direction: column;
  justify-content: flex-start;
}

.card-content h3 {
  display: flex;
  width: 80%;
  margin: 0 0 4px 0;
  font-size: 16px;
  color: #181818;
  word-wrap: break-word;

}

.card-content p {
  margin: 0 0 4px 0;
  font-size: 14px;
  word-wrap: break-word;
}

.card-content small {
  font-size: 12px;
  color: gray;
  word-wrap: break-word;
}

.img {
  position: relative;
  right: -180px;
  width: 20px;
  height: 20px;
}

</style>
