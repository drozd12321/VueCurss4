<template>
  <div class="gl">
    <form class="item1" @submit.prevent="submit">
      <label for="type">Тип блока</label>
      <select
        id="tp"
        @input="$emit('update:type', $event.target.value)"
        :value="type"
      >
        <option v-for="opt in option" :value="opt.value">
          {{ opt.text }}
        </option>
      </select>
      <label for="znach">Значение</label>
      <textarea
        name="zn"
        id="znach"
        :value="aria"
        @input="$emit('update:aria', $event.target.value)"
      ></textarea>
      <button :disabled="!isEnable" class="btn" type="submit">Отправить</button>
    </form>
    <div>
      <button class="btn" @click="$emit('load')">Загрузить комментарии</button>
    </div>
  </div>
</template>
<script>
export default {
  emits: ["update:aria", "update:type", "submit", "load"],
  props: {
    type: String,
    aria: String,
    option: Array,
    isEnable: Boolean,
    load: Boolean,
  },
  methods: {
    submit() {
      this.$emit("submit");
    },
  },
};
</script>
<style>
.gl {
  flex: 0.35;
}
.btn {
  padding: 6px;
  margin: 6px;
  font-size: 15px;
  border: none;
  border-radius: 7px;
  color: white;
  background-color: rgb(43, 42, 42);
  margin-top: 10px;
}
button:disabled {
  background-color: gray;
}
.item1 {
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
