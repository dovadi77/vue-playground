<template>
  <div>
    <h1>{{ msg }}</h1>
    <ul class="list-group" v-for="task in tasks" :key="task.id">
      <li class="list-group-item">{{ `${task.title} : ${task.desc}` }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  props: {
    msg: String,
    tasks: Array,
  },
};
</script>
