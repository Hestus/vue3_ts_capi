<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Manas Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order By Title</button>
        <button @click="handleClick('salary')">Order By Salary</button>
        <button @click="handleClick('location')">Order By Location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobList.vue";
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "farmworker",
        location: "lon lon ranch",
        salary: 300000,
        id: "1",
      },
      {
        title: "quarryMan",
        location: "death mountain",
        salary: 400000,
        id: "2",
      },
      {
        title: "Flute Player",
        location: "the lost woods",
        salary: 350000,
        id: "3",
      },
      {
        title: "Fisherman",
        location: "lake hylia",
        salary: 210000,
        id: "4",
      },
      {
        title: "farmworker",
        location: "lon lon ranch",
        salary: 300000,
        id: "1",
      },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
