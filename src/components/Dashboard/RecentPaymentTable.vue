<template>
    <v-container style="padding: 0 10px 20px 0;">
      <v-data-table-server
        style="box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.3);"
        v-model:items-per-page="itemsPerPage"
        :headers="headers"
        :items-length="totalItems"
        :items="serverItems"
        :loading="loading"
        item-value="name"
        @update:options="loadItems"
        :header-props="{ class: 'custom-header' }"
      >
      </v-data-table-server>
    </v-container>
  </template>
  
  <script>
  const desserts = [
    {
      ID: '1',
      name: 'Rayven Clores',
      address: 'Paniman, Caramoan, Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '2',
      name: 'Emmanuel V. Collao',
      address: 'San Felipe, Naga City, Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '3',
      name: 'Voun Irish Florence C. Dejumo',
      address: 'Pacol, Naga City, Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '4',
      name: 'Hans Gabriel Candor',
      address: 'Somewhere in Naga City Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '5',
      name: 'Jeno Aldrei Laurente',
      address: 'Milaor Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '6',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '7',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '8',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '9',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '10',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '11',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
    {
      ID: '12',
      name: 'Rayven Clores',
      address: 'Paniman Caramoan Camarines Sur',
      date: '02/24/2024',
      amount: 500,
    },
  ]
  
  const FakeAPI = {
    async fetch({ page, itemsPerPage, sortBy }) {
      return new Promise(resolve => {
        setTimeout(() => {
          const start = (page - 1) * itemsPerPage
          const end = start + itemsPerPage
          const items = desserts.slice()
  
          if (sortBy.length) {
            const sortKey = sortBy[0].key
            const sortOrder = sortBy[0].order
            items.sort((a, b) => {
              const aValue = a[sortKey]
              const bValue = b[sortKey]
              return sortOrder === 'desc' ? bValue - aValue : aValue - bValue
            })
          }
  
          const paginated = items.slice(start, end)
  
          resolve({ items: paginated, total: items.length })
        }, 500)
      })
    },
  }
  
  export default {
    data: () => ({
      itemsPerPage: 9,
      headers: [
        {
          title: 'ID',
          align: 'start',
          sortable: false,
          key: 'ID',
        },
        { title: 'Name', key: 'name', align: 'start' },
        { title: 'Address', key: 'address', align: 'start' },
        { title: 'Date', key: 'date', align: 'start' },
        { title: 'Amount', key: 'amount', align: 'end' },
      ],
      serverItems: [],
      loading: true,
      totalItems: 0,
    }),
    methods: {
      loadItems({ page, itemsPerPage, sortBy }) {
        this.loading = true
        FakeAPI.fetch({ page, itemsPerPage, sortBy }).then(({ items, total }) => {
          this.serverItems = items
          this.totalItems = total
          this.loading = false
        })
      },
    },
  }
  </script>
  
  <style>
  
  </style>