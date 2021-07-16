<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : null, 'task']"
  >
    <h3>{{ task.task }}</h3>
    <span @click="$emit('delete-task', task.id)">Delete</span>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object,
  },
}
</script>

<style scope>
.task {
  background: #e8e8e8;
  border: 1px solid #e8e8e8;
  border-radius: 6px;
  margin: 1em 0;
  padding: 0.1em 0 0.1em 2em;
  position: relative;
}

span {
  display: inline;
  color: rgb(248, 79, 79);
  font-size: 0.8em;
  position: absolute;
  top: 0;
  right: 0;
  cursor: pointer;
}

.reminder {
  border-left: 4px solid #1bb146;
}
</style>
