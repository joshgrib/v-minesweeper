<template>
  <div>
    <p>Game board</p>
    <table class="center bordered">
      <tbody>
        <tr
          v-for="i in rows"
          :key="i"
        >
          <td
            v-for="j in cols"
            :key="j"
          >
            <minesweeper-cell
              :value="i === j ? '|>' : `${i} - ${j}`"
            />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import MinesweeperCell from './MinesweeperCell'

export default {
  name: 'MinesweeperGame',
  components: { MinesweeperCell },
  props: {
    rows: {
      type: Number,
      default () { return 10; }
    },
    cols: {
      type: Number,
      default () { return 10; }
    },
    flags: {
      type: Number,
      default () { return 10; }
    }
  }
}
</script>

<style>
table.center {
  text-align: center;
  margin-left: auto;
  margin-right: auto;
}
table.bordered,
table.bordered td {
  border: 1px solid black;
}
</style>
