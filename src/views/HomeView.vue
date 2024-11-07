<template>
  <div>
      <h1>Empleados</h1>
      <p>Filtros:</p>
      <div class="bg-cyan-darken-3 d-flex align-md-center">

        <span class="mr-2">
          Salario desde: 
        </span>
          <input type="number" v-model="from" class="text-white border-md rounded-pill mr-2  bg-cyan-darken-4" />

          <span class="mr-2">
            Salario hasta: 
          </span>
            <input type="number" v-model="to" class="text-white border-md rounded-pill mr-2  bg-cyan-darken-4" />

          <span class="mr-2">
            Edad:
          </span>

        <select class="d-flex text-white bg-cyan-darken-4" v-model="selected" label="Edad" :items="ages">
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
          v-for="employee in employees.data"
          :key="employee.id"
        >
          <td>{{ employee.employee_name }}</td>
          <td>{{ employee.employee_age }}</td>
          <td>{{ employee.employee_salary }} €</td>
          {{ info }}
        </tr>
      </tbody>
    </v-table>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from "axios";

const from = 0
const info = null
const to = 0
const selected = 'a'
const ages = [
        { text: '30 - 35', value: '1' },
        { text: '35 - 40', value: '2' },
        { text: '40 - 45', value: '3' },
        { text: '45 - 50', value: '3' },
        { text: '50 - 55', value: '3' },
        { text: '55 - 60', value: '3' },
      ]
const employees= 
  {"status":"success","data":[{"id":1,"employee_name":"Tiger Nixon","employee_salary":320800,"employee_age":61,"profile_image":""},{"id":2,"employee_name":"Garrett Winters","employee_salary":170750,"employee_age":63,"profile_image":""},{"id":3,"employee_name":"Ashton Cox","employee_salary":86000,"employee_age":66,"profile_image":""},{"id":4,"employee_name":"Cedric Kelly","employee_salary":433060,"employee_age":22,"profile_image":""},{"id":5,"employee_name":"Airi Satou","employee_salary":162700,"employee_age":33,"profile_image":""},{"id":6,"employee_name":"Brielle Williamson","employee_salary":372000,"employee_age":61,"profile_image":""},{"id":7,"employee_name":"Herrod Chandler","employee_salary":137500,"employee_age":59,"profile_image":""},{"id":8,"employee_name":"Rhona Davidson","employee_salary":327900,"employee_age":55,"profile_image":""},{"id":9,"employee_name":"Colleen Hurst","employee_salary":205500,"employee_age":39,"profile_image":""},{"id":10,"employee_name":"Sonya Frost","employee_salary":103600,"employee_age":23,"profile_image":""},{"id":11,"employee_name":"Jena Gaines","employee_salary":90560,"employee_age":30,"profile_image":""},{"id":12,"employee_name":"Quinn Flynn","employee_salary":342000,"employee_age":22,"profile_image":""},{"id":13,"employee_name":"Charde Marshall","employee_salary":470600,"employee_age":36,"profile_image":""},{"id":14,"employee_name":"Haley Kennedy","employee_salary":313500,"employee_age":43,"profile_image":""},{"id":15,"employee_name":"Tatyana Fitzpatrick","employee_salary":385750,"employee_age":19,"profile_image":""},{"id":16,"employee_name":"Michael Silva","employee_salary":198500,"employee_age":66,"profile_image":""},{"id":17,"employee_name":"Paul Byrd","employee_salary":725000,"employee_age":64,"profile_image":""},{"id":18,"employee_name":"Gloria Little","employee_salary":237500,"employee_age":59,"profile_image":""},{"id":19,"employee_name":"Bradley Greer","employee_salary":132000,"employee_age":41,"profile_image":""},{"id":20,"employee_name":"Dai Rios","employee_salary":217500,"employee_age":35,"profile_image":""},{"id":21,"employee_name":"Jenette Caldwell","employee_salary":345000,"employee_age":30,"profile_image":""},{"id":22,"employee_name":"Yuri Berry","employee_salary":675000,"employee_age":40,"profile_image":""},{"id":23,"employee_name":"Caesar Vance","employee_salary":106450,"employee_age":21,"profile_image":""},{"id":24,"employee_name":"Doris Wilder","employee_salary":85600,"employee_age":23,"profile_image":""}],"message":"Successfully! All records has been fetched."}


onMounted(() => {
  // axios
  // .get('https://vip.regardervideos.com/api/main/get_employees', {
  //   headers: {
  //     'Accept': 'application/json',
  //     'Content-Type': 'application/json',
  //     'Access-Control-Allow-Origin': '*',
  //     'Access-Control-Allow-Methods': 'POST, GET, DELETE, PUT, PATCH, OPTIONS'
  //   }
  // })

  
  // .then(response => (this.info = response.data))
  // .catch(error => console.log("Error:", error));

  // fetch('https://cors-anywhere.herokuapp.com/https://vip.regardervideos.com/api/main/get_employees')
  //     .then(response => response.json())
  //     .then(json => console.log(json))

// axios
//   .get('https://dummyjson.com/users')
//   .then(response => (this.info = response.data))
//   .catch(error => console.log("Error:", error));
})

</script>