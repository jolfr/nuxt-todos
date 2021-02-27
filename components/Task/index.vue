<template>
  <div
    class="border-1 border-gray-500 rounded-full shadow-md hover:shadow-lg inline-flex justify-between overflow-x-auto"
    :class="task.state"
  >
    <label class="checkbox inline px-2">
      <input type="checkbox" :checked="isChecked" name="archived" />
    </label>
    <div class="title inline px-2">
      {{ task.title }}
    </div>
    <label class="checkbox inline px-2">
      <input type="checkbox" :checked="isChecked" name="pinned" />
    </label>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: {
      type: Object,
      required: true,
      default: () => ({ id: '', state: '', title: '' }),
      validator: (task) => ['id', 'state', 'title'].every((key) => key in task),
    },
  },
  computed: {
    isChecked() {
      return this.task.state === 'TASK_ARCHIVED'
    },
  },
}
</script>
