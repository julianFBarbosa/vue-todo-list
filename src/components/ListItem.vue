<script>
export default {
  name: "ListItem",
  props: {
    item: {
      type: Object,
      required: true,
    },
    list: {
      type: Array,
      required: true,
    },
  },
};
</script>

<template>
  <li class="list-item" :key="item.key">
    <p class="list-text">{{ item.text }}</p>
    <button class="list-button" v-on:click="$emit('remove-item', item)">
      Finish
    </button>
  </li>
</template>

<style lang="scss" scoped>
@import "../styles/variables";

.list {
  &-item {
    display: flex;
    padding: 8px 0 !important;
    justify-content: space-between;
    align-items: flex-start;

    &:not(:nth-child(1)) {
      border-top: 1px solid $blue-1000_opaque;
    }
  }

  &-button {
    padding: 8px 16px;
    border: none;
    background: $blue-900;
    color: $blue-200;
    font-weight: 550;
  }
}
</style>
