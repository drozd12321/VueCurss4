<template>
  <div class="rezum">
    <div class="it" v-for="(dt, i) in date" :key="i">
      <h1 v-if="dt.tupe === 'h1'">
        {{ dt.are }}
        <hr />
      </h1>
      <h3 v-else-if="dt.tupe === 'h3'">{{ dt.are }}</h3>
      <p v-else-if="dt.tupe === 'p'">{{ dt.are }}</p>
      <img v-else-if="dt.tupe === 'img'" :src="dt.are" alt="image" />
    </div>
  </div>
</template>
<script>
export default {
  props: {
    date: Object,
  },
};
</script>
<style>
.it {
  width: 100%;
  text-align: center;
  word-wrap: break-word;
}
.rezum {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
hr {
  width: 100%;
}
img {
  border-radius: 10px;
}
h1 {
  font-size: 35px;
}
h3 {
  font-weight: 600;
}
</style>
