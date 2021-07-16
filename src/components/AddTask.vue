<template>
  <form @submit="onSubmit">
    <label for="task">Task:</label>
    <input v-model="text" id="task" type="text" placeholder="task" />
    <label id="labelReminder" for="reminder">Reminder:</label>
    <input v-model="reminder" id="reminder" type="checkbox" />
    <button id="submit">Save</button>
  </form>
</template>

<script>
import Button from './Button.vue'

var getTime = () => {
  let months = [
    'January',
    'Feburary',
    'March',
    'April',
    'May',
    'June',
    'July',
    'August',
    'September',
    'October',
    'November',
    'December',
  ]

  const today = new Date()
  const month = today.getMonth()
  const dayte = today.getDate()
  const time = today.getHours()
  const minutes = today.getMinutes()
  return `${months[month]} ${dayte} ${time - 12}:${
    minutes < 10 ? '0' + minutes : minutes
  } `
}

export default {
  components: { Button },
  name: 'AddTask',
  data() {
    return {
      text: '',
      day: '',
      reminder: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      if (!this.text) {
        alert('Please add a task before submitting')
        ReadableStreamDefaultController
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        task: this.text,
        day: getTime(),
        reminder: this.reminder,
      }

      this.$emit('add-task', newTask)

      // reset
      this.text = ''
      this.day = ''
      this.reminder = false
    },
  },
}
</script>

<style scoped>
form {
  display: flex;
  flex-wrap: wrap;
  background: #d4dce0;
  padding: 0.5em;
  border-radius: 6px;
}

input#task {
  width: 100%;
  padding: 0.5em 0.25em;
  font-size: 1em;
  background: #c8d1d6;
  border: none;
  color: black;
}

input#reminder {
  position: relative;
  top: 0.48em;
  left: 0.5em;
}

button#submit {
  border: 1px solid rgb(15, 15, 15);
  background: rgb(15, 15, 15);
  color: white;
  padding: 0.5em 1em;
  width: 100%;
  border-radius: 6px;
  cursor: pointer;
}

button#submit:hover {
  background: black;
}
</style>
