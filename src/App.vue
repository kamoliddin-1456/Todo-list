<script setup>
import { ref } from 'vue'

const newTask = ref('')

const tasks = ref([
  'I will wake up at 8 in the morning',
  'I will practice html for 1 hour',
  'I will give time for 2 hours css',
  'Then I will have breakfast'
])

// Yangi vazifa qo'shish
function addTask() {
  const task = newTask.value.trim()

  // Input bo'sh bo'lsa, hech narsa qilmaydi
  if (task === '') return

  // Yangi vazifani ro'yxatning boshiga qo'shadi
  tasks.value.unshift(task)

  // Inputni bo'shatadi
  newTask.value = ''
}

// Vazifani o'chirish
function deleteTask(index) {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12 m-5">

        <!-- Input va Add tugmasi -->
        <div class="d-flex gap-3 mb-5">
          <input
              v-model="newTask"
              type="text"
              class="form-control"
              placeholder="Enter a task"
              @keyup.enter="addTask"
          />

          <button
              type="button"
              class="btn btn-primary"
              @click="addTask"
          >
            Add
          </button>
        </div>

        <!-- Vazifalar ro'yxati -->
        <div class="list-group">

          <div
              v-for="(task, index) in tasks"
              :key="index"
              class="list-group-item d-flex justify-content-between align-items-center mb-2"
          >
            <span>{{ task }}</span>

            <button
                type="button"
                class="btn btn-primary"
                @click="deleteTask(index)"
            >
              🗑
            </button>
          </div>

        </div>

      </div>
    </div>
  </div>
</template>



<style scoped>

</style>
