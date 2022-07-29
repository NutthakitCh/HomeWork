<template>
  <div class="radio-outline">
    <v-radio :value="value" color="#faac6e" :on-icon="icon"
      ><template #label
        ><span class="radio-label">{{ label }}</span></template
      ></v-radio
    >
  </div>
</template>

<script>
import { mdiCheckboxMarkedCircle } from '@mdi/js'
export default {
  props: {
    label: {
      type: String,
      default: '',
    },
    value: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return { icon: mdiCheckboxMarkedCircle }
  },
}
</script>

<style lang="css" scoped>
.radio-outline {
  outline: 1px solid #f3f3f3;
  border-radius: 6px;
  padding: 15px;
  margin-bottom: 8px;
}
.radio-label {
  color: #000 !important;
}
</style>
