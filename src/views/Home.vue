<template>
  <div class="home">
    <div class="home__container">
      <HomeHeader />
      <HomeContent />
      <UserPanel />
    </div>
  </div>
</template>

<script>
import HomeHeader from "@/components/views/home/HomeHeader.vue";
import HomeContent from "@/components/views/home/HomeContent.vue";
import UserPanel from "@/components/views/home/UserPanel.vue";

export default {
  components: {
    HomeHeader,
    HomeContent,
    UserPanel,
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/colors.scss";
@import "@/scss/media-query.scss";

.home {
  padding: 10px;
  background: $gray;
  width: 100vw;
  height: 100vh;
  overflow-x: hidden;
  overflow-y: hidden;
  color: white;

  &__container {
    background-image: url("../assets/home.jpg");
    height: 100%;
    background-size: cover;
    background-position-x: center;
    background-position-y: center;
    display: grid;
    grid-template-rows: 0.3fr 1.7fr 1fr;
  }
}
</style>
