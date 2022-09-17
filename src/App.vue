<template>
  <div class="todo-container">
    <h1 class="todo-header">Твой TO DO</h1>

    <div class="add">
      <input
        type="text"
        placeholder="Добавить новую задачу"
        class="add__input"
        maxlength="35"
        v-model="tasks.name"
        @keypress.enter="addTask"
      >
      <button
        class="add-button"
        @click="addTask"
      >+</button>
    </div>

    <ul class="task-list">
      <li
        class="task-list__item"
        v-for="task in tasks"
        :key="task.id"
      >
        <label class="task-list__item-label">
          <input type="checkbox">
          <span>{{task.name}}</span>
        </label>
        <button
          class="delete-button"
          @click="removeTask(task)"
        ></button>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { name: 'Первая задча', id: 1 },
        { name: 'Velit aliquip nostrud est consequat proident dolor Lorem ea ex consectetur dolore consectetur do ut.', id: 2 },
        { name: 'Третья задча', id: 3 },
        { name: 'Четвертая задча', id: 4 },
        { name: 'Пятая задча', id: 5 },
        { name: 'Шестая задча', id: 6 },
      ]


    }
  },
  methods: {
    addTask() {
      if (!this.tasks.name) {
        return
      }
      this.tasks.push({
        name: this.tasks.name,
      })
      this.tasks.name = ''
    },
    removeTask(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1)
    }
  },
}

</script>

