<template>
  <div class="container">
    <img src="~/assets/rafiki.png" alt="" />
    <div class="text-container">
      <p class="orange">ขอบคุณที่เข้าร่วมกิจกรรม</p>
      <p class="small">
        เจ้าหน้าที่จะทำการติดต่อท่านไปตามข้อมูลที่ท่าน<br />ได้ทำการลงทะเบียนหากท่านได้รับรางวัล
      </p>
      <p class="small">
        <span class="big">ประกาศผลกิจกรรมใน</span><br />วันที่ 5 สิงหาคม 2565<br />เวลา
        18.00 น.
      </p>
    </div>

    <footerButtonVue lable="เสร็จสิ้น" @btn-click="handleClick" />
  </div>
</template>

<script>
import footerButtonVue from '../components/footerButton.vue'

export default {
  name: 'FinishPage',
  components: { footerButtonVue },

  data() {
    return {}
  },
  head() {
    return {
      title: 'Finish',
    }
  },
  methods: {
    handleClick() {
      const liff = window.liff
      liff.closeWindow()
    },
  },
}
</script>

<style lang="css">
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px;
  gap: 40px;

  height: 100vh;
}

/* image background */
.container::after {
  content: '';
  position: absolute;
  background-image: url(~/assets/finishBg.jpg);
  background-size: cover;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  opacity: 0.2;
  z-index: -1;
}

.text-container {
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.orange {
  font-weight: 600;
  font-size: 26px;
  color: #ef4123;
}

.small {
  font-size: 14px;
}

.big {
  font-weight: 700;
  font-size: 20px;
}
</style>
