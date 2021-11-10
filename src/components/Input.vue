<template>
  <input :type="type" :placeholder="placeholder" />
</template>

<script>
export default {
  props: {
    placeholder: String,
    type: String,
  },
};
</script>

<style lang="scss">
input {
  border: unset;
  outline: unset;
  font-family: Rubik, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 18px;
  padding: 8px 10px 8px 10px;
  font-weight: 300;
  border-radius: 10px;
}
</style>
