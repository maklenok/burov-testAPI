<template>
  <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">

    <main class="px-3">
      <h1>Сайт Сергея Бабатчикова</h1>
      <p class="lead">Уроженец Новосибирска, студент ВКИ НГУ</p>
    </main>
    <div class="container">
  <v-simple-table dark>
    <template v-slot:default>
      <thead>
      <tr>
        <th class="text-left">
          Время
        </th>
        <th class="text-left">
          Занятие
        </th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(schedule,index) in schedule" :key="index">

        <td>{{schedule.scheduletime }}</td>
        <td>{{schedule.scheduleName}}</td>
      </tr>
      </tbody>

    </template>
  </v-simple-table>

    </div>
  </div>

</template>

<script>
import axios from 'axios';

export default {

  data() {
    return {
      schedule: null
    };
  },
  created() {
    axios.get("http://localhost:15210/api/schedule")
        .then(response => this.schedule = response.data);
  }
};
</script>
