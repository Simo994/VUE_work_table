<script setup>
import { ref } from 'vue';
import * as bootstrap from 'bootstrap';

// Создаем реактивные переменные для хранения данных
const items = ref([]);
const newItem = ref({
  tabNumber: '',
  fullName: '',
  email: '',
  phone: '',
  position: ''
});

// Функция для добавления данных
const addData = () => {
  items.value.push({ ...newItem.value });
  newItem.value = {
    tabNumber: '',
    fullName: '',
    email: '',
    phone: '',
    position: ''
  };
};
const Delete = (index) => {
  
    items.value.splice(index, 1);
  
}
</script>

<template>
  <div class="wrapper">
    <header class="d-flex flex-wrap justify-content-center py-3 mb-4 border-bottom">
      <a href="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none">
        <svg class="bi me-2" width="40" height="32">
          <use xlink:href="#bootstrap"></use>
        </svg>
        <span class="fs-4">Simple header</span>
      </a>

      <ul class="nav nav-pills">
        <li class="nav-item"><a href="#" class="nav-link active" aria-current="page">Home</a></li>
        <li class="nav-item"><a href="#" class="nav-link">Features</a></li>
        <li class="nav-item"><a href="#" class="nav-link">Pricing</a></li>
        <li class="nav-item"><a href="#" class="nav-link">FAQs</a></li>
        <li class="nav-item"><a href="#" class="nav-link">About</a></li>
      </ul>
    </header>

    <div class="container">
      <div class="row mb-3 text-center">
        <div class="col-2 themed-grid-col">Таб номер</div>
        <div class="col-3 themed-grid-col">ФИО</div>
        <div class="col-2 themed-grid-col">email</div>
        <div class="col-2 themed-grid-col">телефон</div>
        <div class="col-2 themed-grid-col">должность</div>
      </div>
      <div class="row mb-3 text-center" v-for="(item, index) in items" :key="index">
        <div class="col-2 themed-grid-col">{{ item.tabNumber }}</div>
        <div class="col-3 themed-grid-col">{{ item.fullName }}</div>
        <div class="col-2 themed-grid-col">{{ item.email }}</div>
        <div class="col-2 themed-grid-col">{{ item.phone }}</div>
        <div class="col-2 themed-grid-col">{{ item.position }}</div>
        <div class="col-1 themed-grid-col"><button type="button" class="btn btn-danger" @click="Delete(index)">удалить</button></div>
      </div>
    </div>

    <div class="container">
      <form action="" class="form">
        <input type="text" class="form-control" v-model="newItem.tabNumber" placeholder="Таб номер">
        <input type="text" class="form-control" v-model="newItem.fullName" placeholder="ФИО">
        <input type="email" class="form-control" v-model="newItem.email" placeholder="email">
        <input type="text" class="form-control" v-model="newItem.phone" placeholder="телефон">
        <select name="" id="" class="form-select" v-model="newItem.position">
          <option value="Программист">Программист</option>
          <option value="Грузчик">Грузчик</option>
          <option value="Оператор">Оператор</option>
        </select>

        <button type="button" @click="addData" class="btn btn-primary">Сохранить</button>
      </form>
    </div>

    <footer class="py-3 my-4">
      <ul class="nav justify-content-center border-bottom pb-3 mb-3">
        <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">Home</a></li>
        <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">Features</a></li>
        <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">Pricing</a></li>
        <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">FAQs</a></li>
        <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">About</a></li>
      </ul>
      <p class="text-center text-body-secondary">© 2024 Company, Inc</p>
    </footer>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 20px;
}

.form-control, .form-select {
  width: 100%;
}
</style>