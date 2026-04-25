<template>
    <v-row class="justify-end">
        <div class="mb-6 mt-3">
            <v-btn prepend-icon="$vuetify" class="">Novo Agendamento</v-btn>
        </div>
    </v-row>
   
    <v-data-table-server v-model:items-per-page="itemsPerPage" :items="desserts"
    :items-length="totalItems" :loading="loading" :search="search" item-value="produto" @update:options="loadItems">
    </v-data-table-server>

</template>


<script setup>

const desserts = [
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    },
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    },
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    },
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    },
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    },
    {
        cliente: 'Maria Silva',
        service: 'Consulta Oftalmológica',
        dateAndDate: '01/04/2026 09:00',
        status: 'confirmado'
    }
]
        
    

</script>