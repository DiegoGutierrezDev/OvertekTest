<template>
      <h1>Empleados</h1>
      <p>Filtros:</p>
      <div class="bg-cyan-darken-3 d-flex align-md-center">

        <label for="salary_from" class="mr-2">
          Salario desde: 
        </label>
          <input type="number" v-model="this.salary_from" class="text-white border-md rounded-pill mr-2 bg-cyan-darken-4" />

          <label for="salary_to" class="mr-2">
            Salario hasta: 
          </label>
            <input type="number" v-model="this.salary_to" class="text-white border-md rounded-pill mr-2 bg-cyan-darken-4" />

          <label class="mr-2" for="age">
            Edad:
          </label>

        <select class="d-flex text-white bg-cyan-darken-4" v-model="selectedAge" label="Edad" :value="ages">
          <option v-for="age in ages" :value="age.value">
              {{ age.text }}
          </option>
        </select>
      </div>
    <v-table theme="dark">
      <thead>
        <tr>
          <th class="text-left">
            Nombre del empleado
          </th>
          <th class="text-left">
            Edad
          </th>
          <th class="text-left">
            Salario
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="employee in filteredByAgeEmployees"
          :key="employee.id"
        >
        {{ salary_from }}
          <td>{{ employee.employee_name }}</td>
          <td>{{ employee.employee_age }}</td>
          <td>{{ employee.employee_salary }} €</td>
          {{ info }}
        </tr>
      </tbody>
    </v-table>
</template>

<script setup>
import { computed, onMounted, reactive,ref } from 'vue'
import axios from "axios";

/**Data */
const filters = ref({
  salary_from: 0,
  salary_to: 0,
  age_from: 0,
  age_to: 0,

})
const info = null
const salary_to = 99999
const ages = [
        { from: 30, to: 35 },
        { from: 35, to: 40 },
        { from: 40, to: 45 },
        { from: 45, to: 50 },
        { from: 50, to: 55 },
        { from: 55, to: 60 },
        { from: 60, to: 65 },
      ]
const age = { from: 30, to: 35 }

let employees= 
 [{"id":1,"employee_name":"Tiger Nixon","employee_salary":320800,"employee_age":61,"profile_image":""},{"id":2,"employee_name":"Garrett Winters","employee_salary":170750,"employee_age":63,"profile_image":""},{"id":3,"employee_name":"Ashton Cox","employee_salary":86000,"employee_age":66,"profile_image":""},{"id":4,"employee_name":"Cedric Kelly","employee_salary":433060,"employee_age":22,"profile_image":""},{"id":5,"employee_name":"Airi Satou","employee_salary":162700,"employee_age":33,"profile_image":""},{"id":6,"employee_name":"Brielle Williamson","employee_salary":372000,"employee_age":61,"profile_image":""},{"id":7,"employee_name":"Herrod Chandler","employee_salary":137500,"employee_age":59,"profile_image":""},{"id":8,"employee_name":"Rhona Davidson","employee_salary":327900,"employee_age":55,"profile_image":""},{"id":9,"employee_name":"Colleen Hurst","employee_salary":205500,"employee_age":39,"profile_image":""},{"id":10,"employee_name":"Sonya Frost","employee_salary":103600,"employee_age":23,"profile_image":""},{"id":11,"employee_name":"Jena Gaines","employee_salary":90560,"employee_age":30,"profile_image":""},{"id":12,"employee_name":"Quinn Flynn","employee_salary":342000,"employee_age":22,"profile_image":""},{"id":13,"employee_name":"Charde Marshall","employee_salary":470600,"employee_age":36,"profile_image":""},{"id":14,"employee_name":"Haley Kennedy","employee_salary":313500,"employee_age":43,"profile_image":""},{"id":15,"employee_name":"Tatyana Fitzpatrick","employee_salary":385750,"employee_age":19,"profile_image":""},{"id":16,"employee_name":"Michael Silva","employee_salary":198500,"employee_age":66,"profile_image":""},{"id":17,"employee_name":"Paul Byrd","employee_salary":725000,"employee_age":64,"profile_image":""},{"id":18,"employee_name":"Gloria Little","employee_salary":237500,"employee_age":59,"profile_image":""},{"id":19,"employee_name":"Bradley Greer","employee_salary":132000,"employee_age":41,"profile_image":""},{"id":20,"employee_name":"Dai Rios","employee_salary":217500,"employee_age":35,"profile_image":""},{"id":21,"employee_name":"Jenette Caldwell","employee_salary":345000,"employee_age":30,"profile_image":""},{"id":22,"employee_name":"Yuri Berry","employee_salary":675000,"employee_age":40,"profile_image":""},{"id":23,"employee_name":"Caesar Vance","employee_salary":106450,"employee_age":21,"profile_image":""},{"id":24,"employee_name":"Doris Wilder","employee_salary":85600,"employee_age":23,"profile_image":""}]

  /**Computed properties */

  const filteredEmployees = computed(() => {
    // if (!salary_from )
    console.log('salary_from')
    console.log(salary_from)
    console.log(employees.data.filter((employee) => employee.employee_salary > 90000))
  return employees.data.filter((employee) => employee.employee_salary > salary_from)
  return employees.data > salary_from && employees.data < salary_to
})

const filteredAges = computed(() => {
  
})
</script>