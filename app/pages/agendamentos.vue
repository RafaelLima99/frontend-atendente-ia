<template>
    <v-row class="justify-end">
        <div class="mb-6 mt-3">
            <v-btn prepend-icon="$vuetify" class="">Novo Agendamento</v-btn>
        </div>
    </v-row>
   

    <v-table class="border-sm">
        <thead>
            <tr>
                <th class="text-left">
                    Cliente
                </th>
                <th class="text-left">
                    Serviço
                </th>
                <th class="text-left">
                    Data/Hora
                </th>
                <th class="text-left">
                    Status
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in desserts" :key="item.name">
                <td>{{ item.cliente }}</td>
                <td>{{ item.service }}</td>
                <td>{{ item.dateAndDate }}</td>
                <td>{{ item.status }}</td>
            </tr>
        </tbody>
    </v-table>
</template>


<script>
export default {
    data() {
        return {
            desserts: [
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
            ],
        }
    },
}
</script>