<template>
    <v-data-table
            :headers="headers"
            :items="filteredData"
            item-key="name"
        >
        <template
            v-for="(header, i) in headers"
            v-slot:[`header.${header.value}`] = "{ }"
        >
        {{ header.text }}
            <div @click.stop :key="i">
                <v-text-field
                    :key = "i"
                    v-model="multiSearch[header.value]"
                    class="pa"
                    type="text"
                    :placeholder="header.value"
                ></v-text-field>
            </div>
        </template>
        </v-data-table>
</template>
<script>
export default {
    name: 'DataTable',
  data() {
    return {
        multiSearch:{},
        headers: [
          {text: 'Dessert', value: 'name',},
          { text: 'Calories', value: 'calories' },
          { text: 'Fat (g)', value: 'fat' },
          { text: 'Carbs (g)', value: 'carbs' },
          { text: 'Protein (g)', value: 'protein' },
          { text: 'Iron (%)', value: 'iron' },
        ],
      rowItems: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%',
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%',
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%',
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%',
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%',
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%',
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%',
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%',
        },
        {
          name: 'Donut Choco',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
        },
        {
          name: 'Donut Vanilla',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
        },
        {
          name: 'Donut Strawberry',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%',
        },
      ],
    }
  },
  computed: {
    filteredData() {
        if(this.multiSearch){
            return this.rowItems.filter((item) => {
                return Object.entries(this.multiSearch).every(([key, value]) => {
                    return (item[key] || "").toString().toUpperCase().includes(value.toString().toUpperCase())
                })
            })
        } else {
            return this.rowItems
        }
    }
  }
}
</script>