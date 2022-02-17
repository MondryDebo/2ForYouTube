<template>
  <input type="text"
    id="search"
    name="search"
    placeholder="Paste YouTube link here"
    :value="value"
    @input="handleChange"
  />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
}
</script>

<style lang="scss" scoped>
  input {
    width: 75%;
    height: 50px;
    padding: 8.5px 0 8.5px 40px;
    border-radius: 15px;
    border: 2px solid rgb(189, 189, 189);
    background: url('../assets/search-outline.svg');
    background-repeat: no-repeat;
    background-size: 30px;
    background-position: 7.5px 7.5px;
  }
</style>