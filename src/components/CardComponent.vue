<script>
export default {
  props: {
    card: Object,
  },
  data() {
    return {
      isModalOpen: false,
      editableCard: { ...this.card },
    };
  },

  methods: {
    openEditModal() {
      this.editableCard = { ...this.card };
      this.isModalOpen = true;
    },
    closeEditModal() {
      this.isModalOpen = false;
    },
    saveChanges() {
      this.$emit("update-card", this.editableCard);
      this.closeEditModal();
    },
  },


};
</script>

<template>
  <div class="card_container">
    <div class="card">
      <div class="card-header">
        <h3>{{ card.title }}</h3>
        <img src="../assets/img/edit.png" class="edit-icon" alt="Edit" @click="openEditModal" />
      </div>
      <div class="card-content">
        <p>{{ card.text }}</p>
        <small>{{ card.note }}</small>
      </div>
    </div>

    <div v-if="isModalOpen" class="modal-overlay" @click="closeEditModal">
      <div class="modal-content" @click.stop>
        <h3>Редактировать карточку</h3>
        <label>
          Заголовок:
          <input type="text" v-model="editableCard.title" />
        </label>
        <label>
          Текст:
          <textarea v-model="editableCard.text"></textarea>
        </label>
        <label>
          Заметка:
          <input type="text" v-model="editableCard.note" />
        </label>
        <button @click="saveChanges">Сохранить</button>
        <button @click="closeEditModal">Отмена</button>
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
  flex-direction: column;
  margin: 2px 4px;
  width: 85%;
  min-height: 60px;
  padding: 10px;
  background-color: #fff;
  border: 1px solid lightgreen;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  position: relative;
  margin-bottom: 4px;
}

.card-header h3 {
  font-size: 16px;
  color: #181818;
  margin: 0;
  padding-right: 24px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.edit-icon {
  display: flex;
  position: absolute;
  top: 0;
  right: 0;
  width: 20px;
  height: 20px;
  cursor: pointer;
  align-items: center;
  justify-content: center;
}
  .card-content p {
    margin: 0 0 4px 0;
    font-size: 14px;
    word-wrap: break-word;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .card-content small {
    font-size: 12px;
    color: gray;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

.modal-overlay {
  display: flex;
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.7);
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  display: flex;
  width: 300px;
  padding: 20px;
  background: #fff;
  border-radius: 8px;
  flex-direction: column;
  justify-content: space-between;
}

.modal-content h3 {
  margin-top: 0;
}

.modal-content label {
  margin-bottom: 10px;
}

.modal-content input,
.modal-content textarea {
  display: flex;
  width: 284px;
  margin-top: 5px;
  margin-bottom: 15px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.modal-content button {
  margin-top: 10px;
  padding: 8px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>

