<template>
  <div class="activity-item px-4">
    <v-row align="center" justify-lg="left" style="color:rgb(var(--v-theme-title));" no-gutters>
      <v-col cols="2" sm="1" md="auto" class="d-flex" :class="{
        'mr-0': smAndDown,
        'mr-2': mdAndUp
      }">
        <v-avatar :size="smAndDown ? 40 : 40" class="mb-4">
          <v-img v-if="icon" :src="icon"></v-img>
          <v-icon v-else size="xxx-large">mdi-account-circle</v-icon>
        </v-avatar>
      </v-col>

      <v-col class="text-no-wrap scrollable px-3 fill-height py-0">
        <v-card-text class="font-weight-bold pa-0">{{ user }}</v-card-text>
        <v-card-text class="text-caption pa-0 mt-0.5 text-sm-caption" style="color:rgb(var(--v-theme-text_caption))">{{
          transaction_type }}</v-card-text>
        <v-card-text class="d-flex align-center text-caption pa-0 mt-0.5"
          style="color:rgb(var(--v-theme-text_caption))">
          <v-icon size="x-small" class="mr-1" color="button">mdi-circle</v-icon>
          {{ payment_type }}
        </v-card-text>
      </v-col>

      <v-col class="text-right text-no-wrap" style="margin-left: auto;">
        <v-card-text class="font-weight-bold pa-0" :class="{ 'text-success': !out }">
          {{ out ? '-' + amount : '+' + amount }}
        </v-card-text>
        <v-card-text class="text-caption pa-0 mt-0.5" style="color:rgb(var(--v-theme-text_caption))">{{ time
          }}</v-card-text>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
import { useDisplay } from 'vuetify'
const { smAndDown, mdAndUp } = useDisplay()

const props = defineProps({
  user: {
    type: String,
    required: true
  },
  transaction_type: {
    type: String,
    required: true
  },
  payment_type: {
    type: String,
    required: true
  },
  amount: {
    type: String,
    required: true
  },
  time: {
    type: String,
    required: true
  },
  out: {
    type: Boolean,
    required: true
  },
  icon: {
    type: String,
    default: null
  }
})

defineOptions({
  name: 'ActivityItem'
})
</script>

<style scoped>
.v-card {
  margin-bottom: 8px;
}

.scrollable {
  overflow: scroll;
  overflow-y: hidden;
}

.scrollable::-webkit-scrollbar {
  width: 0px;
  background: transparent;
}

.activity-item {
  background-color: transparent !important;
}
</style>