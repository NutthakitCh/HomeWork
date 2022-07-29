<template>
  <div>
    <registerHeader />
    <div v-if="onLoading"></div>
    <div v-else>
      <v-form ref="form" class="form-container">
        <!-- name input -->
        <p class="input-label">ชื่อ - นามสกุล {{ user_id }}</p>
        <p class="description-label">(ใช้เพื่อจับฉลาก และ ประกาศรางวัล)</p>
        <v-text-field
          v-model="name"
          color="#E0E0E0"
          placeholder="ชื่อ นามสกุล"
          outlined
          required
        ></v-text-field>

        <!-- phone input -->
        <p class="input-label">เบอร์ติดต่อ</p>
        <p class="description-label">(ใช้เพื่อจับฉลาก และ ประกาศรางวัล)</p>
        <v-text-field
          v-model="phone"
          color="#E0E0E0"
          placeholder="0xxxxxxxxx"
          outlined
        ></v-text-field>

        <!-- address input -->
        <p class="input-label">ที่อยู่ในการจัดส่ง</p>
        <p class="description-label">(ใช้เพื่อจับฉลาก และ ประกาศรางวัล)</p>
        <v-textarea
          v-model="address"
          auto-grow
          outlined
          color="#E0E0E0"
          rows="3"
        ></v-textarea>

        <!-- answer input -->
        <p class="input-label">
          คุณรู้หรือไม่ว่า !
          <span class="highlight"><span>6</span> เมนู</span>ในแอปพลิเคชัน GHB
          ALL มีอะไรบ้าง ?
        </p>
        <v-radio-group v-model="answer" column>
          <radioItem
            v-for="choice in choices"
            :key="choice.value"
            :label="choice.label"
            :value="choice.value"
          />
        </v-radio-group>

        <!-- feedback input -->
        <p class="input-label">
          ท่านอยากให้มีเมนูหรือฟีเจอร์อะไรเพิ่มเติมอีกบ้าง
        </p>
        <v-textarea
          v-model="feedback"
          placeholder="โปรดระบุ?"
          auto-grow
          outlined
          color="#F3F3F3"
          rows="3"
        ></v-textarea>

        <p class="description-label center-text">
          หมายเหตุ : กรุณากรอกข้อมูลให้ถูกต้องครบถ้วน
          เพื่อประโยชน์ในการร่วมกิจกรรมของท่าน
        </p>
      </v-form>
      <footerButton lable="ส่งคำตอบ" @btn-click="handleClick" />
    </div>
  </div>
</template>

<script>
import registerHeader from '../components/registerHeader.vue'
import footerButton from '../components/footerButton.vue'
import radioItem from '../components/radioItem.vue'

// import axios from 'axios'
export default {
  name: 'IndexPage',
  components: { registerHeader, footerButton, radioItem },
  data() {
    return {
      liff: {},
      onLoading: false,
      name: '',
      phone: '',
      address: '',
      answer: '',
      feedback: '',
      user_id: '',
      choices: [
        {
          label: 'พร้อมเพย์, สินเชื่อ, เงินกู้, โอนเงิน, ใบเสร็จ, เปิดบัญชี',
          value: 1,
        },
        {
          label:
            'สินเชื่อ, เงินกู้, เงินฝาก, โอนเงิน, ใบเสร็จ, ชำระเงินกู้/ค่าบริการอื่นๆ',
          value: 2,
        },
        {
          label:
            'พร้อมเพย์, สินเชื่อ, เงินฝาก, โอนเงิน, ชำระเงินกู้/ค่าบริการอื่นๆ, ใบเสร็จ',
          value: 3,
        },
        {
          label: 'เปิดบัญชี, พร้อมเพย์, สินเชื่อ, โอนเงิน, เงินฝาก, ถอนเงิน',
          value: 4,
        },
      ],
    }
  },
  head() {
    return {
      title: 'Register',
    }
  },
  async mounted() {
    this.liff = window.liff

    await this.liff.init({
      liffId: '1655139052-26m30wBe',
    })

    if (this.liff.isLoggedIn()) {
      this.user_id = await this.liff.getProfile().userId
    } else {
      await this.liff.login()
    }

    this.onLoading = false
  },
  methods: {
    handleClick() {
      this.onLoading = false
      // prepare data
      const data = {
        name: this.name,
        phone: this.phone,
        address: this.address,
        answer: this.answer,
        feedback: this.feedback,
        user_id: this.user_id,
      }
      console.log(data)

      // request api
      try {
        // await axios.post('https://ghbank-online-activity.digitalsetup.co/api/v1/register_06_2022', data)
        // Go to finish Page
        // this.$router.push('/finish')
      } catch (err) {
        this.onLoading = false
      }
    },
  },
}
</script>

<style lang="css">
.form-container {
  padding: 15px;
  padding-bottom: 110px;
}
.input-label {
  font-weight: 800;
  font-size: 20px;
  line-height: 30px;
  color: #383838;
}

.description-label {
  font-weight: 400;
  font-size: 12px;
  line-height: 18px;
  color: #bdbdbd;
  margin-bottom: 10px;
}

.center-text {
  text-align: center;
  padding: 0 30px;
}

.highlight {
  color: red;
}

.highlight span {
  font-size: 32px;
}
</style>
