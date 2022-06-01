<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>{{ task.text }}</h3>
    <p>{{ task.day }}</p>
    <Button @click="DeleteTask(task.id)" name="Delete" color="red" />
  </div>
</template>
<script>
import Button from "./Button.vue";
export default {
  name: "Task",
  components: {
    Button,
  },
  props: {
    task: Object,
  },
  methods: {
    DeleteTask(id) {
      console.log(id);
      this.$emit("delete-task", id);
    },
  },
};
</script>

<style>
.task {
  background-color: rgb(214, 207, 207);
  padding: 10px;
  margin: 5px 0;
  width: 25%;
  border-radius: 5px;
}
.reminder {
  border-left: solid green 5px;
}
</style>
