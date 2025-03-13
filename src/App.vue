<script>
export default {
  data() {
    return {
      options: [
        {
          value: "h1",
          text: "Заголовок",
        },
        {
          value: "p",
          text: "Текст",
        },
        {
          value: "h3",
          text: "Подзаголовок",
        },
        {
          value: "img",
          text: "Фото",
        },
      ],
      tp: "h1",
      area: "",
    };
  },
  methods: {
    handleSubmit() {
      this.tp = "h1";
      this.area = "";
    },
  },
};
</script>

<template>
  <div class="container">
    <form class="item1" @submit.prevent="handleSubmit">
      <label for="type">Тип блока</label>
      <select id="tp" v-model="tp">
        <option v-for="opt in options" :value="opt.value">
          {{ opt.text }}
        </option>
      </select>
      <label for="znach">Значение</label>
      <textarea name="zn" id="znach" v-model="area"></textarea>
      <button class="btn" type="submit">Отправить</button>
    </form>
    <div class="item2"></div>
  </div>
</template>

<style scoped>
.btn {
  padding: 6px;
  margin: 6px;
  font-size: 15px;
  border: none;
  border-radius: 7px;
  color: white;
  background-color: rgb(43, 42, 42);
}
.container {
  display: flex;
  gap: 50px;
  margin-right: auto;
  margin-top: 20px;
  background-color: rgb(248, 248, 245);
  justify-content: center;
  height: 800px;
  border-radius: 10px;
}
.item1 {
  flex: 0.35;
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  height: 50%;
  border-radius: 10px;
  padding: 7px;
}
label {
  margin-top: 30px;
  font-size: 20px;
}
.item2 {
  flex: 0.5;
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  height: auto;
  margin-bottom: 5px;
  border-radius: 10px;
  padding: 7px;
  overflow-y: scroll;
}
textarea {
  width: 100%;
  height: 150px;
  color: black;
  border-radius: 10px;
  margin: auto;
  outline: none;
  border: none;
  resize: none;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
select {
  width: 100%;
  color: black;
  border-radius: 3px;
  margin: auto;
  outline: none;
  border: none;
  resize: none;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  background-color: white;
  padding: 5px;
  font-size: 15px;
  border-radius: 6px;
}
option {
  font-size: 15px;
  background-color: white;
}
</style>
