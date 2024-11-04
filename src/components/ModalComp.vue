<script>
export default {
  props: {
    show: {
      type: Boolean,
      required: true
    }
  },
  data() {
    return {
      title: '',
      cardText: '',
      note: ''
    };
  },
  methods: {
    handleSubmit() {
      this.$emit('save', { title: this.title, cardText: this.cardText, note: this.note });
      this.title = '';
      this.cardText = '';
      this.note = '';
    }
  }
};
</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="modal_mask">
      <div class="modal_container">
        <div class="modal_header">
          <label for="title">Заголовок:</label>
          <input v-model="title" id="title" type="text" placeholder="Введите заголовок" />
        </div>
        <div class="modal_body">
          <label for="cardText">Текст карточки:</label>
          <textarea v-model="cardText" id="cardText" placeholder="Введите текст карточки"></textarea>
        </div>
        <div class="modal_footer">
          <label for="note">Примечание:</label>
          <input v-model="note" id="note" type="text" placeholder="Введите примечание" />
        </div>
        <button class="modal_btn" @click="handleSubmit">Сохранить</button>
        <button class="modal_btn" @click="$emit('close')">Отмена</button>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.modal_mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal_container {
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  width: 300px;
  display: flex;
  flex-direction: column;
}

.modal_header,
.modal_body,
.modal_footer {
  margin: 10px 0;
}

input,
textarea {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
}

textarea {
  height: 70px;
  resize: none;
}

.modal_btn {
  display: flex;
  margin-top: 10px;
  padding: 8px;
  width: 300px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  justify-content: center;
}

</style>
