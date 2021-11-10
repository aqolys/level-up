<template>
  <button
    class="button"
    :class="[
      { 'button-text': text, 'button-icon': icon, 'button--small': small },
      color ? `button--${color}` : '',
    ]"
    :title="title"
    :style="[hexColor ? { background: hexColor } : '']"
  >
    <img :src="require(`@/assets/icons/${icon}`)" :alt="icon" v-if="icon" />
    {{ text }}
  </button>
</template>

<script>
export default {
  props: {
    icon: String,
    text: String,
    color: String,
    title: String,
    small: Boolean,
    hexColor: String,
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/colors.scss";

.button {
  color: white;
  font-size: 18px;
  font-weight: 400;
  border-radius: 10px;
  transition: all 0.1 ease;

  &-text {
    padding: 13px 50px;
    box-shadow: 0px 4px 0px #ffffff;

    &:active {
      transform: translateY(4px);
      box-shadow: unset;
    }
  }

  &-icon {
    display: flex;
    justify-content: center;
    align-items: center;
    min-width: 30px;
    min-height: 30px;
    max-width: 40px;
    max-height: 40px;
    border-radius: 100%;

    img {
      max-width: 35px;
    }
  }

  &--small {
    padding: 13px 20px;
  }

  &--blue {
    background: $blue;
  }

  &--dark-blue {
    background: $dark-blue;
  }

  &--purple {
    background: $purple;
  }

  &--pink {
    background: $pink;
  }

  &--orange {
    background: $orange;
  }

  &--green {
    background: $green;
  }

  &--red {
    background: $red;
  }

  &--black {
    background: $black;
  }

  &--gray {
    background: $gray;
  }
}
</style>