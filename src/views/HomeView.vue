<template>
      <h1>Empleados</h1>
      <p>Filtros:</p>
      <div class="bg-cyan-darken-3 d-flex align-md-center">

      <label for="salary_from" class="mr-2">
        Salario desde: 
      </label>
      <input id="salary_from" type="number" v-model="filters.salary_from" class="text-white border-md rounded-pill mr-2 bg-cyan-darken-4" />

      <label for="salary_to" class="mr-2">
        Salario hasta: 
      </label>
        <input id="salary_to" type="number" v-model="filters.salary_to" class="text-white border-md rounded-pill mr-2 bg-cyan-darken-4" />

      <label for="ages" class="mr-2"> Edad: </label>
      <select id="ages" class="d-flex text-white bg-cyan-darken-4" v-model="filters.age">
        <option v-for="age in ages" :key="age.from" :value="age">
          {{ age.from }} - {{ age.to }}
        </option>
      </select>
      </div>

    <div v-if="!filteredEmployees.length">No existen empleados con el criterio de búsqueda</div>
    <v-table v-else theme="dark">
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
          <th></th>
        </tr>
      </thead>

      <tbody>
        <tr
          v-for="employee in filteredEmployees"
          :key="employee.id"
          :class="{
          'bg-green-darken-2': employee.employee_salary < 100000,
          'bg-red-darken-2': employee.employee_salary > 500000}"
        >

          <td >{{ employee.employee_name }}</td>
          <td>{{ employee.employee_age }}</td>
          <td>{{ employee.employee_salary }} €</td>

          <div v-if="employee.employee_salary > 500000" height="24px" width="24px" class="d-flex align-center justify-content">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" height="24px" width="24px">
          <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v3.75m-9.303 3.376c-.866 1.5.217 3.374 1.948 3.374h14.71c1.73 0 2.813-1.874 1.948-3.374L13.949 3.378c-.866-1.5-3.032-1.5-3.898 0L2.697 16.126ZM12 15.75h.007v.008H12v-.008Z" />
          </svg>

          </div>
            <td v-else></td>
        </tr>
      </tbody>
    </v-table>
</template>

<script setup>
import axios from 'axios';
import { computed, onMounted, ref } from 'vue'

/**Data */
const filters = ref({
  salary_from: 0,
  salary_to: 10000000,
  age: {
    from: 0,
    to: 100
  }

})
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

let employees_list = 
 [{"id":1,"employee_name":"Tiger Nixon","employee_salary":320800,"employee_age":61,"profile_image":""},{"id":2,"employee_name":"Garrett Winters","employee_salary":170750,"employee_age":63,"profile_image":""},{"id":3,"employee_name":"Ashton Cox","employee_salary":86000,"employee_age":66,"profile_image":""},{"id":4,"employee_name":"Cedric Kelly","employee_salary":433060,"employee_age":22,"profile_image":""},{"id":5,"employee_name":"Airi Satou","employee_salary":162700,"employee_age":33,"profile_image":""},{"id":6,"employee_name":"Brielle Williamson","employee_salary":372000,"employee_age":61,"profile_image":""},{"id":7,"employee_name":"Herrod Chandler","employee_salary":137500,"employee_age":59,"profile_image":""},{"id":8,"employee_name":"Rhona Davidson","employee_salary":327900,"employee_age":55,"profile_image":""},{"id":9,"employee_name":"Colleen Hurst","employee_salary":205500,"employee_age":39,"profile_image":""},{"id":10,"employee_name":"Sonya Frost","employee_salary":103600,"employee_age":23,"profile_image":""},{"id":11,"employee_name":"Jena Gaines","employee_salary":90560,"employee_age":30,"profile_image":""},{"id":12,"employee_name":"Quinn Flynn","employee_salary":342000,"employee_age":22,"profile_image":""},{"id":13,"employee_name":"Charde Marshall","employee_salary":470600,"employee_age":36,"profile_image":""},{"id":14,"employee_name":"Haley Kennedy","employee_salary":313500,"employee_age":43,"profile_image":""},{"id":15,"employee_name":"Tatyana Fitzpatrick","employee_salary":385750,"employee_age":19,"profile_image":""},{"id":16,"employee_name":"Michael Silva","employee_salary":198500,"employee_age":66,"profile_image":""},{"id":17,"employee_name":"Paul Byrd","employee_salary":725000,"employee_age":64,"profile_image":""},{"id":18,"employee_name":"Gloria Little","employee_salary":237500,"employee_age":59,"profile_image":""},{"id":19,"employee_name":"Bradley Greer","employee_salary":132000,"employee_age":41,"profile_image":""},{"id":20,"employee_name":"Dai Rios","employee_salary":217500,"employee_age":35,"profile_image":""},{"id":21,"employee_name":"Jenette Caldwell","employee_salary":345000,"employee_age":30,"profile_image":""},{"id":22,"employee_name":"Yuri Berry","employee_salary":675000,"employee_age":40,"profile_image":""},{"id":23,"employee_name":"Caesar Vance","employee_salary":106450,"employee_age":21,"profile_image":""},{"id":24,"employee_name":"Doris Wilder","employee_salary":85600,"employee_age":23,"profile_image":""}]




  /**Computed properties */

  const filteredEmployees = computed(() => {
  let employees = employees_list.filter((employee) => {
    return (
      (employee.employee_salary >= filters.value.salary_from &&
      employee.employee_salary <= filters.value.salary_to) &&
      (employee.employee_age >= filters.value.age.from &&
      employee.employee_age <= filters.value.age.to)
    )
  })

  return employees
})

 /**
 * Lifecycle
 */

 onMounted(async () => {
  await axios
    .get('https://vip.regardervideos.com/api/main/get_employees', {
      headers: {
        Accept: 'application/json',
        'Content-Type': 'application/json',
        'Access-Control-Allow-Origin': '*'
      },
    })
    .then((response) => console.log(response))
    .catch((error) => console.log(error))
})

</script>