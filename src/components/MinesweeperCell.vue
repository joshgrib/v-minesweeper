<template>
  <div>
    <span
      v-if="!revealed"
      key="hidden"
    >
      ...
    </span>
    <span
      v-else-if="isFlag"
      key="flag"
    >
      |>
    </span>
    <span
      v-else
      key="neighbor-flag-count"
    >
      {{ neighborFlags }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'MinesweeperCell',
  props: {
    revealed: {
      type: Boolean
    },
    isFlag: {
      type: Boolean
    },
    neighborFlags: {
      type: Number,
      default () { return 0; }
    }
  }
}
</script>
