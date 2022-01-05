<template>
  <div class="home__header">
    <div class="home__header__date home__header-item">
      <span v-for="item in date" :key="item">
        {{ item }}
      </span>
    </div>
    <div class="home__header__logo home__header-item">
      <img src="@/assets/home-logo.png" alt="Логотип" />
    </div>
    <div class="home__header__user home__header-item">
      <div class="home__header__user-avatar">
        <img src="@/assets/user.png" alt="" />
      </div>
      <div class="home__header__user-info">
        <span class="home__header__user-name">Ильин Даниил</span>
        <div class="home__header__user-balance">
          <span>10 000</span>
          <img src="@/assets/coin.png" />
        </div>
      </div>
      <div class="home__header__user-actions">
        <Button icon="exit.svg" color="red" title="Выйти" />
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  data() {
    return {
      date: null,
    };
  },
  created() {
    moment.locale("ru");
    this.date = moment().format("YYYY/MMMM, D/dd").split("/");
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/colors.scss";
@import "@/scss/media-query.scss";

.home__header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;

  &-item {
    background: $gray;

    &:nth-child(1) {
      padding: 0 8px 8px 0;
      border-radius: 0 0 20px 0;
      justify-self: start;
    }

    &:nth-child(2) {
      padding: 0 8px 8px 8px;
      border-radius: 0 0 20px 20px;
      justify-self: center;
      background: unset;
    }

    &:nth-child(3) {
      padding: 0 0 8px 8px;
      border-radius: 0 0 0 45px;
      justify-self: end;
    }
  }

  &__date {
    background: $black;
    padding: 10px;
    display: flex;
    gap: 6px;
    border: 0 5px 5px 0 solid $gray;
    border-radius: 0 20px 20px 0;

    span {
      background: $purple;
      padding: 6px;
      border-radius: 10px;
    }
  }

  &__logo {
    margin-top: -11px;

    @include extra-large-desktops {
      img {
        width: 500px;
      }
    }
  }

  &__user {
    display: flex;

    &-avatar {
      display: flex;
      align-items: center;
      background: $black;
      padding: 8px;
      border-radius: 100% 0 0 100%;
    }

    &-info {
      background: $black;
      padding: 8px;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
    }

    &-balance {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    &-actions {
      background: $black;
      padding: 10px 10px 0 20px;
    }
  }
}
</style>
