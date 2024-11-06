    <template>
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
          v-for="item in desserts"
          :key="item.name"
        >
          <td>{{ employee.name }}</td>
          <td>{{ employee.age }}</td>
          <td>{{ employee.salary }}</td>
        </tr>
      </tbody>
    </v-table>
</template>

<script setup>
</script>