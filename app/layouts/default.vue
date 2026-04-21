
<template>
    <v-layout class="rounded rounded-md border">
        <v-navigation-drawer v-model="drawer">
            <v-list-item prepend-avatar="https://randomuser.me/api/portraits/men/78.jpg" title="John Leider">
            </v-list-item>

            <v-divider></v-divider>

            <v-list density="compact">
                <v-list-subheader>Agenda</v-list-subheader>

                <v-list-item v-for="(item, i) in items" :key="i" :value="item" :to="item.to" color="primary">

                    <template v-slot:prepend>
                        <v-icon :icon="item.icon"></v-icon>
                    </template>

                    <v-list-item-title to="">{{ item.text }}</v-list-item-title>

                </v-list-item>
            </v-list>
        </v-navigation-drawer>

        <v-app-bar title="Atendente IA">
            <template v-slot:prepend>
                <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            </template>
            
        </v-app-bar>

        <v-main>
            <v-container>
                <slot />
            </v-container>
        </v-main>
    </v-layout>
</template>

<script setup>
    import { ref, watch } from 'vue'

    const drawer = ref(true)
    const group = ref(null)

    watch(group, () => {
        drawer.value = true
    })

    const items = [
    { text: 'Agendamentos', icon: 'mdi-clock', to: '/agendamentos' },
    { text: 'Disponibilidade', icon: 'mdi-account', to: '/disponibilidade' },
     { text: 'Horário de Funcionamento', icon: 'mdi-account', to: '/horario-funcionamento' }
  ]

</script>