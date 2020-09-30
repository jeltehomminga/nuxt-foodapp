<template>
  <div>
    <label>
      What {{ select }} do you want?
      <select @change="$emit('change', $event.target.value)">
        <option value>Please select a value</option>
        <option v-for="option in selectOptions" :key="option" :value="option">{{
          option
        }}</option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  props: {
    select: {
      type: String,
      default: "cuisine"
    },
    selectOptions: {
      type: Array,
      default: () => ["tacos", "pizza", "dim sum"]
    }
  }
};
</script>

<style lang="scss" scoped></style>
