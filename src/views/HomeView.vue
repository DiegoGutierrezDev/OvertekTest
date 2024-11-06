<template>
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
          v-for="employee in employees"
          :key="item.name"
        >
          <td>{{ employee.name }}</td>
          <td>{{ employee.age }}</td>
          <td>{{ employee.salary }}</td>
        </tr>
      </tbody>
    </v-table>
</template>

<script>
export default {
  data() {
    return {
      from: 0,
      to: 0,
      selected: 'A',
      ages: [
        { text: '30 - 35', value: '1' },
        { text: '35 - 40', value: '2' },
        { text: '40 - 45', value: '3' },
        { text: '45 - 50', value: '3' },
        { text: '50 - 55', value: '3' },
        { text: '55 - 60', value: '3' },
      ],
      employees: []
    }
  }
}
</script>