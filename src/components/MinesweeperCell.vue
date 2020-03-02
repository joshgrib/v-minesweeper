<template>
  <div @click="reveal">
    <span v-if="!hidden">
      {{ value }}
    </span>
    <span v-else>
      ...
    </span>
  </div>
</template>

<script>
export default {
  name: 'MinesweeperCell',
  props: {
    value: {
      type: String,
      default () { return ''; }
    }
  },
  data () {
    return {
      hidden: true
    }
  },
  methods: {
    reveal () {
      this.hidden = false;
    }
  }
}
</script>
