<template>
  <div class="user__panel">
    <div class="user__panel-secondary">
      <div class="user__panel-mailing">
        <Input type="email" placeholder="Email..." />
        <Button text="Подписка" color="orange" style="padding: 10px 40px" />
      </div>
      <div class="user__panel-auth">
        <img src="@/assets/user.png" />
        <Button text="Вход" color="red" style="padding: 10px 50px" />
      </div>
    </div>
    <div class="user__panel-primary">
      <img class="user__panel-background" src="@/assets/panel-rectangle.svg" />
      <div class="user__panel-content">
        <div class="user__panel-top">
          <Button icon="vk.png" title="ВКонтакте" />
          <Button icon="facebook.png" title="Facebook" />
          <div class="user__panel-dots">
            <span
              v-for="n in 8"
              :key="n"
              @click="$refs.carousel.goTo(n - 1)"
            ></span>
          </div>
          <Button icon="instagram.png" title="Instagram" />
          <Button icon="telegram.png" title="Телеграм" />
        </div>
        <div class="user__panel-grid">
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
          <div class="user__panel-profession">
            <div class="user__panel-profession__title">Профессии</div>
            <div class="user__panel-profession__wrapper">
              <span class="user__panel-profession__dotted-line"></span>
              <ul class="user__panel-profession__list">
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
          <div class="user__panel-group user__panel-group--black">
            <Button text="UB" small hexColor="#A6D608" />
            <Button text="UX" small hexColor="#15AA9D" />
            <Button text="PD" small hexColor="#05857A" />
          </div>
          <Button text="Магазины" color="green" />
          <Button text="Новости" color="purple" />
          <Button text="Инструкция" color="pink" />
          <div class="user__panel-group">
            <Button text="Отзывы" small color="orange" style="width: 50%" />
            <Button text="Чат-бот" small color="dark-blue" style="width: 50%" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "@/components/Button.vue";
import Input from "@/components/Input.vue";

export default {
  components: {
    Button,
    Input,
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/colors.scss";
@import "@/scss/media-query.scss";

.user__panel {
  margin-bottom: -14px;
  display: flex;
  justify-content: center;

  @include extra-large-desktops {
    &-background {
      width: 1080px;
    }
  }

  &-primary {
    position: relative;
  }

  &-background {
    user-select: none;
    pointer-events: none;
  }

  &-secondary {
    background: $black;
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
    background-image: url("../../../assets/panel-left-side-rectangle.svg");
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
</style>
