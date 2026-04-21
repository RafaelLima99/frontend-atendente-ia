<template>
    <div>
        <h1 class="text-title-large">Disponibilidade</h1>
        <h2 class="text-label-large">Configure os dias e horários disponíveis para agendamento</h2>
    </div>

    <v-row>
        <v-col>
            <v-btn class="mb-5">
                Salvar Alterações
            </v-btn>
            <v-card class="pa-4">
                <h1 class="text-title-medium mb-4">Horários por dia da semana</h1>
                <v-sheet class="pa-3 mb-4" color="grey-lighten-3" rounded="lg">
                    <v-row density="compact">
                        <v-col cols="12" sm="12" md="4">
                            <v-switch v-model="model" :label="`Segunda Feira`" hide-details class="mt-n2"></v-switch>
                        </v-col>
                        <v-col cols="12" sm="12" md="5">
                            <v-text-field :model-value="time" label="Horário" variant="outlined" density="compact" class="mb-n4"
                                prepend-icon="mdi-clock-time-four-outline" readonly>
                                <v-menu v-model="showMenu" :close-on-content-click="false" activator="parent"
                                    min-width="0">
                                    <v-time-picker v-model="time"></v-time-picker>
                                </v-menu>
                            </v-text-field>
                        </v-col>
                    </v-row>
                </v-sheet>

                <v-sheet class="pa-3 mb-4" color="grey-lighten-3" rounded="lg">
                    <v-row density="compact">
                        <v-col cols="12" sm="12" md="4">
                            <v-switch v-model="model2" :label="`Terça Feira`" hide-details class="mt-n2"></v-switch>
                        </v-col>
                        <v-col cols="12" sm="12" md="5">
                            <v-text-field :model-value="time2" label="Horário" variant="outlined" density="compact" class="mb-n4"
                                prepend-icon="mdi-clock-time-four-outline" readonly>
                                <v-menu v-model="showMenu2" :close-on-content-click="false" activator="parent"
                                    min-width="0">
                                    <v-time-picker v-model="time2"></v-time-picker>
                                </v-menu>
                            </v-text-field>
                        </v-col>
                    </v-row>
                </v-sheet>
            </v-card>
        </v-col>
    </v-row>
</template>


<script setup>
import { ref } from 'vue'

const model = ref('no')
const model2 = ref('no')

const time = ref(null)
const showMenu = ref(false)
const showDialog = ref(false)


const time2 = ref(null)
const showMenu2 = ref(false)
const showDialog2 = ref(false)

</script>