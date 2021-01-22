<template>
  <div class="home">
    <div>
      <div class="home--header">SKY - KO</div>
      <div class="home--details">
        Virual game, real money
        <span>Avaiable soon on Android and IOS</span>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  &--header {
    font-size: 70px;
    letter-spacing: 20px;
    font-weight: 700;
    z-index: 10;
    text-shadow: 3px 3px 6px black;
  }
  &--details {
    font-size: 30px;
    font-weight: 300;
    margin-top: 51px;
    text-shadow: 3px 3px 6px black;
    display: flex;
    flex-direction: column;
    padding-bottom: 250px;

    span {
      font-size: 15px;
      font-weight: 400;
      justify-self: flex-end;
    }
  }
}
</style>
