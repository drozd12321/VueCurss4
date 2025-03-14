<script>
import { computed } from "vue";
import AppForm from "./components/AppForm.vue";
import AppRezume from "./components/AppRezume.vue";
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
      date: [],
      comments: [
        { id: 1, value: "comment 1" },
        { id: 2, value: "comment 2" },
        { id: 3, value: "comment 3" },
        { id: 4, value: "comment 4" },
        { id: 5, value: "comment 5" },
        { id: 6, value: "comment 6" },
        { id: 7, value: "comment 7" },
        { id: 8, value: "comment 8" },
        { id: 9, value: "comment 9" },
        { id: 10, value: "comment 10" },
        { id: 11, value: "comment 11" },
        { id: 12, value: "comment 12" },
      ],
      load: false,
    };
  },
  methods: {
    handleSubmit() {
      this.date.push({
        tupe: this.tp,
        are: this.area,
      });
      console.log(this.date);
      this.tp = "h1";
      this.area = "";
    },
  },
  computed: {
    valiadateForm() {
      return this.area.length > 3;
    },
  },

  components: { AppForm, AppRezume },
};
</script>

<template>
  <div class="container">
    <AppForm
      @submit="handleSubmit"
      v-model:type="tp"
      v-model:aria="area"
      :option="options"
      :isEnable="valiadateForm"
      @load="load = true"
    ></AppForm>
    <div class="item2">
      <AppRezume :date="date"></AppRezume>
    </div>
  </div>
  <div v-if="load" class="container1">
    <h1>Комментарии</h1>
    <div class="inf" v-for="com in comments">
      <span>{{ com.id }}:</span>
      <span>{{ com.value }}</span>
    </div>
  </div>
</template>

<style scoped>
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
.item2 {
  flex: 0.6;
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
.container1 {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 20px;
  background-color: rgb(248, 248, 245);
  height: 500px;
  border-radius: 10px;
  width: 100%;
  overflow-y: scroll;
}
.inf {
  width: 70%;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  height: 300px;
  border-radius: 10px;
  display: flex;
  gap: 10px;
  align-items: center;
  margin-left: 30px;
  padding: 20px;
  margin-top: 10px;
}
h1 {
  text-align: center;
}
</style>
