<template>
  <table border="1" class="bg-gray-300 border-2 border-blue-400">
    <thead>
      <tr>
        <td v-for="col in cols" :key="col.id" class="bg-white">
          {{ col.text }}
        </td>
      </tr>
    </thead>
    <tbody>
      <tr v-for="row in rows" :key="row.id">
        <td v-for="col in cols" :key="col.id" class="bg-white">
          <slot :name="col.id" :row="row" :col="col">
            {{ row[col.id] }}
          </slot>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  props: {
    rows: {
      type: Array,
      default() {
        return [
          { id: 111, code: '6501001', name: 'Name 1', age: 25 },
        ]
      },
    },
    cols: {
      type: Array,
      default() {
        return [
          { id: 'code', text: 'รหัสนักเรียน', width: '100px' },
          { id: 'name', text: 'ชื่อ - นามสกุล' },
        ]
      },
    },
  },
}
</script>
