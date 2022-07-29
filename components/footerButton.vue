<template>
  <div class="footer">
    <button class="btn" @click="emitClick">{{ lable }}</button>
  </div>
</template>

<script>
export default {
  props: {
    lable: {
      type: String,
      default: 'ส่งคำตอบ',
    },
  },
  methods: {
    emitClick() {
      // emit click to parent
      this.$emit('btn-click')
    },
  },
}
</script>

<style lang="css" scoped>
.footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  background-color: #fff;
  padding: 20px 15px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.btn {
  height: 52px;
  width: 100%;
  color: #fff;
  background-color: #ef4123;
  border-radius: 50px;
}

.btn:hover {
  opacity: 0.8;
}
</style>
