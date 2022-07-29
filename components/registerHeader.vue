<template>
  <div class="header inner-center">
    <span class="header-text">ลงทะเบียน</span>
  </div>
</template>

<script>
export default {}
</script>

<style lang="css" scoped>
.header {
  position: relative;
  top: 0;
  width: 100%;
  height: 67px;
  background-color: #ef4123;
  color: #fff;
}

.header-text {
  font-size: 1.5em;
  font-weight: bold;
  text-shadow: 1px 1px 0 #000, -1px -1px 0 #000, 1px -1px 0 #000,
    -1px 1px 0 #000, 1px 1px 0 #000;
}

/* image background */
.header::after {
  content: '';
  position: absolute;
  background-image: url(~/assets/headerImage.png);
  background-position: bottom;
  background-size: cover;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  opacity: 0.22;
}

/* center child content */
.inner-center {
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
}
</style>
