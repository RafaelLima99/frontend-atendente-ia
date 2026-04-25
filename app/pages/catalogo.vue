<template>
    <div>
        <h1 class="text-title-large">Catálogo</h1>

        <v-row>
            <v-col cols="6">
                <h2 class="text-label-large">Gerencie seus produtos e serviços</h2>
            </v-col>
            <v-col cols="6" class="mb-6 mt-3">
                <v-row class="justify-end">
                    <v-btn prepend-icon="$vuetify" class="">Novo Produto</v-btn>
                </v-row>
            </v-col>
        </v-row>
    </div>

    <v-row>
        <v-col>
            <v-data-table-server v-model:items-per-page="itemsPerPage" :headers="headers" :items="serverItems"
                :items-length="totalItems" :loading="loading" :search="search" item-value="produto"
                @update:options="loadItems">


                <template v-slot:item.actions="{ item }">
                    <div class="d-flex ga-2 justify-end">
                        <v-icon color="medium-emphasis" icon="mdi-pencil" size="small" @click="edit(item.id)"></v-icon>

                        <v-icon color="medium-emphasis" icon="mdi-delete" size="small"
                            @click="remove(item.id)"></v-icon>
                    </div>
                </template>
            </v-data-table-server>
        </v-col>
    </v-row>

    <v-dialog v-model="dialog" max-width="500">
        <v-card :subtitle="`${isEditing ? 'Update' : 'Create'} your favorite book`"
            :title="`${isEditing ? 'Edit' : 'Add'} a Book`">
            <template v-slot:text>
                <v-row>
                    <v-col cols="12">
                        <v-text-field v-model="formModel.title" label="Title"></v-text-field>
                    </v-col>

                    <v-col cols="12" md="6">
                        <v-text-field v-model="formModel.author" label="Author"></v-text-field>
                    </v-col>

                    <v-col cols="12" md="6">
                        <v-select v-model="formModel.genre" :items="['Fiction', 'Dystopian', 'Non-Fiction', 'Sci-Fi']"
                            label="Genre"></v-select>
                    </v-col>

                    <v-col cols="12" md="6">
                        <v-number-input v-model="formModel.year" :max="currentYear" :min="1"
                            label="Year"></v-number-input>
                    </v-col>

                    <v-col cols="12" md="6">
                        <v-number-input v-model="formModel.pages" :min="1" label="Pages"></v-number-input>
                    </v-col>
                </v-row>
            </template>

            <v-divider></v-divider>

            <v-card-actions class="bg-surface-light">
                <v-btn text="Cancel" variant="plain" @click="dialog = false"></v-btn>

                <v-spacer></v-spacer>

                <v-btn text="Save" @click="save"></v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
</template>


<script setup>

import { ref } from 'vue'
const desserts = [
    {
        produto: 'Consulta Oftalmológica',
        type: 'Preço fixo',
        valor: 6,
        actions: 24
    },
    {
        produto: 'Óculos de Grau Completo',
        type: 'A partir de',
        valor: 0,
        actions: 94
    },
    {
        produto: 'Ajuste de Óculos',
        type: 'Preço fixo',
        valor: 26,
        actions: 65
    },
    {
        produto: 'Troca de Lentes',
        type: 'A partir de',
        valor: 16,
        actions: 23
    },
    {
        produto: 'Exame de Vista',
        type: 'A partir de',
        valor: 16,
        actions: 49
    },
    {
        produto: 'Lentes de Contato',
        type: 'A partir de',
        valor: 9,
        actions: 37
    },
    {
        produto: 'Limpeza de Lentes',
        type: 'A partir de',
        valor: 0.2,
        actions: 98
    },
    {
        produto: 'Cupcake',
        type: 'A partir de',
        valor: 3.7,
        actions: 67
    },
    {
        produto: 'Honeycomb',
        type: 'A partir de',
        valor: 3.2,
        actions: 87
    },
    {
        produto: 'Donut',
        type: 'A partir de',
        valor: 25,
        actions: 51
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
                const paginated = items.slice(start, end === -1 ? undefined : end)
                resolve({ items: paginated, total: items.length })
            }, 500)
        })
    },
}
const itemsPerPage = ref(5)
const headers = ref([
    {
        title: 'Produto',
        align: 'start',
        sortable: false,
        key: 'produto',
    },
    { title: 'Tipo', key: 'type', align: 'end' },
    { title: 'Valor', key: 'valor', align: 'end' },
    { title: 'Ações', key: 'actions', align: 'end' }

])
const search = ref('')
const serverItems = ref([])
const loading = ref(true)
const totalItems = ref(0)
function loadItems({ page, itemsPerPage, sortBy }) {
    loading.value = true
    FakeAPI.fetch({ page, itemsPerPage, sortBy }).then(({ items, total }) => {
        serverItems.value = items
        totalItems.value = total
        loading.value = false
    })
}
</script>

<style>
.-v-data-table-footer__items-per-page {
    display: none;
}
</style>