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
          <button class="modal_btn" @click="handleSubmit">Сохранить</button>
          <button class="modal_btn" @click="$emit('close')">Отмена</button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.modal_mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal_container {
  width: 300px;
  margin: auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal_header,
.modal_body,
.modal_footer {
  margin: 10px 0;
}

.modal_btn {
  float: right;
  margin-left: 10px;
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
  resize: none;
}
</style>
