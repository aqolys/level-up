<template>
  <div class="home">
    <div class="home__container">
      <div class="home__header">
        <div class="home__header-item">
          <div class="home__date">
            <span v-for="item in date" :key="item">
              {{ item }}
            </span>
          </div>
        </div>
        <div class="home__header-item">
          <div class="home__logo">
            <img src="../assets/home-logo.png" alt="Логотип" />
          </div>
        </div>
        <div class="home__header-item">
          <div class="home__user">
            <div class="home__user-avatar">
              <img src="@/assets/user.png" alt="" />
            </div>
            <div class="home__user-info">
              <span class="home__user-name">Ильин Даниил</span>
              <div class="home__user-balance">
                <span>10 000</span>
                <img src="@/assets/coin.png" />
              </div>
            </div>
            <div class="home__user-actions">
              <Button icon="exit.svg" color="red" title="Выйти" />
            </div>
          </div>
        </div>
      </div>
      <div class="home__content">
        <agile :options="agileOptions" ref="carousel">
          <div class="slide" v-for="n in 8" :key="n">
            <h3>Slide {{ n }}</h3>
          </div>
        </agile>
      </div>
      <div class="home__panel">
        <div class="home__panel-secondary">
          <div class="home__panel-mailing">
            <Input type="email" placeholder="Email..." />
            <Button text="Подписка" color="orange" style="padding: 10px 40px" />
          </div>
          <div class="home__panel-auth">
            <img src="@/assets/user.png" alt="" />
            <Button text="Вход" color="red" style="padding: 10px 50px" />
          </div>
        </div>
        <div class="home__panel-primary">
          <img class="home__panel-background" src="@/assets/panel-rectangle.svg" />
          <div class="home__panel-content">
            <div class="home__panel-top">
              <Button icon="vk.png" title="ВКонтакте" />
              <Button icon="facebook.png" title="Facebook" />
              <div class="home__panel-dots">
                <span v-for="n in 8" :key="n" @click="$refs.carousel.goTo(n - 1)"></span>
              </div>
              <Button icon="instagram.png" title="Instagram" />
              <Button icon="telegram.png" title="Телеграм" />
            </div>
            <div class="home__panel-grid">
              <Button
                text="Курсы"
                color="blue"
                style="
                  clip-path: polygon(10% 0%, 100% 0, 100% 120%, -5% 120%);
                  width: 102%;
                  justify-self: right;
                  border-top-left-radius: 50px;
                "
              />
              <div class="home__panel-profession">
                <div class="home__panel-profession__title">Профессии</div>
                <div class="home__panel-profession__wrapper">
                  <span class="home__panel-profession__dotted-line"></span>
                  <ul class="home__panel-profession__list">
                    <li>Дизайнер интерфейсов</li>
                    <li>Интернет маркетолог</li>
                    <li>Цифровой куратор</li>
                    <li>Интернет маркетолог</li>
                    <li>Интернет маркетолог</li>
                    <li>Интернет маркетолог</li>
                    <li>Интернет маркетолог</li>
                    <li>Интернет маркетолог</li>
                  </ul>
                </div>
              </div>
              <Button
                text="Мастер-Классы"
                color="purple"
                style="
                  clip-path: polygon(0 0, 89% 0, 104% 120%, 0% 200%);
                  width: 102%;
                  border-top-right-radius: 50px;
                "
              />
              <div class="home__panel-group home__panel-group--black">
                <Button text="UB" small hexColor="#A6D608" />
                <Button text="UX" small hexColor="#15AA9D" />
                <Button text="PD" small hexColor="#05857A" />
              </div>
              <Button text="Магазины" color="green" />
              <Button text="Новости" color="purple" />
              <Button text="Инструкция" color="pink" />
              <div class="home__panel-group">
                <Button text="Отзывы" small color="orange" style="width: 50%" />
                <Button text="Чат-бот" small color="dark-blue" style="width: 50%" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

import Button from "@/components/Button.vue";
import Input from "@/components/Input.vue";

import { VueAgile } from "vue-agile";

export default {
  data: () => ({
    date: [],
    agileOptions: {
      navButtons: false,
      timing: "ease-in-out",
    },
  }),
  components: {
    Button,
    Input,
    agile: VueAgile,
  },
  created() {
    moment.locale("ru");
    this.date = moment().format("YYYY/MMMM, D/dd").split("/");
  },
};
</script>

<style lang="scss">
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

  &__header {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    align-items: start;

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
  }

  &__user {
    display: flex;
    height: 100%;

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

  &__content {
    width: 100%;
    height: 100%;
    overflow: hidden;

    span {
      width: 100%;
      height: 100%;
      background: red;
    }
  }

  &__panel {
    margin-bottom: -14px;
    display: flex;
    justify-content: center;

    &-primary {
      position: relative;
    }

    &-background {
      user-select: none;
      pointer-events: none;
    }

    &-secondary {
      background: $gray;
      width: calc(100% - 20px);
      height: 160px;
      padding: 10px 0 10px 0;
      position: absolute;
      left: 10px;
      bottom: 0;
      z-index: 0;
      display: flex;
      justify-content: space-between;
    }

    &-content {
      display: flex;
      flex-direction: column;
      position: absolute;
      height: 100%;
      width: 780px;
      top: 0;
      left: calc(50% - 393px);
    }

    &-top {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 10px 0 10px;
      gap: 20px;
    }

    &-dots {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 10px;
      background: $black;
      min-width: 400px;
      border-radius: 10px;
      padding: 10px 0;

      span {
        width: 20px;
        height: 20px;
        border-radius: 100%;
        cursor: pointer;

        &:nth-child(1) {
          background: $pink;
        }

        &:nth-child(2) {
          background: $purple;
        }

        &:nth-child(3) {
          background: $dark-blue;
        }

        &:nth-child(4) {
          background: $blue;
        }

        &:nth-child(5) {
          background: $green;
        }

        &:nth-child(6) {
          background: $yellow;
        }

        &:nth-child(7) {
          background: $orange;
        }

        &:nth-child(8) {
          background: $red;
        }
      }
    }

    &-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      grid-template-rows: 1fr 70px 1fr;
      column-gap: 15px;
      row-gap: 15px;
    }

    &-profession {
      background: $dark-blue;
      grid-row: 1/3;
      grid-column: 2/3;
      border-radius: 10px;
      display: flex;
      flex-direction: column;
      box-shadow: 0px 4px 0px #ffffff;

      &__title {
        padding: 13px;
        text-align: center;
        font-size: 18px;
      }

      &__wrapper {
        background: white;
        margin: 0 15px;
        border-radius: 8px;
        padding: 5px 4px 5px 0;
        position: relative;
      }

      &__list {
        color: black;
        height: 65px;
        overflow-y: scroll;

        li {
          padding: 3px 8px;
          cursor: pointer;
          font-weight: 300;

          &:hover {
            font-weight: 500;
          }
        }

        &::-webkit-scrollbar {
          width: 5px;
        }

        &::-webkit-scrollbar-track {
          background: transparent;
        }

        &::-webkit-scrollbar-thumb {
          border-radius: 25%;
          outline: 0 solid white;
          height: 20px;
          outline-width: 5px 0 5px 0;

          background-color: $black;
        }
      }

      &__dotted-line {
        position: absolute;
        height: calc(100% - 10px);
        right: 5px;
        top: 5px;
        border-left: 3px dotted $black;
      }
    }

    &-group {
      border-radius: 10px;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 15px;

      &--black {
        background: $black;
        box-shadow: 0px 4px 0px #ffffff;
      }
    }

    &-mailing {
      background-image: url("../assets/panel-left-side-rectangle.svg");
      // background-size: contain;
      background-repeat: no-repeat;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: center;
      // height: 100%;
      width: 265px;
      gap: 10px;
      padding: 10px;

      input {
        width: 80%;
      }
    }

    &-auth {
      // background-image: url("../assets/panel-right-side-rectangle.svg");
      background-repeat: no-repeat;
      display: flex;
      flex-direction: column;
      align-items: center;
      // height: 100%;
      width: 265px;
      gap: 10px;
      padding: 10px 10px 10px 90px;

      img {
        width: 55px;
      }
    }
  }

  @include extra-large-desktops {
    &__logo {
      img {
        width: 500px;
      }
    }

    &__panel {
      &-background {
        width: 1080px;
      }
    }
  }
}
</style>
