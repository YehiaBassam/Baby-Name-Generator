<script setup lang="ts">
const items = ref([
  {
    title: "1) Choose a gender",
    options: [
      { label: "Boy", active: false },
      { label: "Girl", active: true },
    ],
  },
  {
    title: "2) Choose the name's popularity",
    options: [
      { label: "Trendy", active: true },
      { label: "Unique", active: false },
    ],
  },
  {
    title: "3) Choose name's length",
    options: [
      { label: "All", active: true },
      { label: "Long", active: false },
      { label: "Short", active: false },
    ],
  },
]);

function borderStyle(index: number, options: Array) {
  let classStytle;
  if (index == 2) 
    classStytle = "option-right";
  else if (index == 1 && options.length == 3) 
    classStytle = "option";
  else if (index == 1 && options.length != 3) 
    classStytle = "option-right";
  else 
    classStytle = "option-left";

  return classStytle;
}

const setActiveClass = (clickedOption: Object, options: Array) => {
  for (const option of options) {
    option.active = false;
  }
  clickedOption.active = true;
};
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>

    <div class="options-container">
      <div v-for="(item, i) in items" :key="i" class="option-container">
        <h4>{{ item.title }}</h4>
        <div class="option-buttons">
          <button
            v-for="(option, j) in item.options"
            :key="j"
            :class="
              borderStyle(j, item.options),
              option.active ? 'option-active' : null
            "
            class="option"
            @click="setActiveClass(option, item.options)"
          >
            {{ option.label }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}
h1 {
  font-size: 3rem;
}
.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}
.option-container {
  margin-bottom: 2rem;
}
.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}
.option-left {
  border-radius: 1rem 0 0 1rem;
}
.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>
