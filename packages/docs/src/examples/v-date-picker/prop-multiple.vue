<template>
  <v-row>
    <v-col
      cols="12"
      sm="6"
    >
      <v-date-picker
        v-model="dates"
        multiple
      ></v-date-picker>
    </v-col>
    <v-col
      cols="12"
      sm="6"
    >
      <v-menu
        ref="menu"
        v-model="menuActive"
        v-model:return-value="dates"
        :close-on-content-click="false"
        min-width="auto"
        transition="scale-transition"
      >
        <template v-slot:activator="{ props }">
          <v-combobox
            v-model="dates"
            label="Multiple picker in menu"
            prepend-icon="mdi-calendar"
            chips
            multiple
            readonly
            v-bind="props"
          ></v-combobox>
        </template>
        <v-date-picker
          v-model="dates"
          multiple
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            variant="text"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            color="primary"
            variant="text"
            @click="menu.save(dates)"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
    </v-col>
  </v-row>
</template>

<script setup>
  import { ref } from 'vue'

  const menu = ref()

  const dates = ref(['2018-09-15', '2018-09-20'])
  const menuActive = ref(false)
</script>

<script>
  export default {
    data: () => ({
      dates: ['2018-09-15', '2018-09-20'],
      menuActive: false,
    }),
  }
</script>
