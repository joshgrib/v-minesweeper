<template>
  <div>
    <p>Game board</p>
    <table class="center bordered">
      <tbody>
        <tr
          v-for="(row, i) in this.board"
          :key="`row-${i}`"
        >
          <td
            v-for="(cell, j) in row"
            :key="`cell-${i}-${j}`"
            @click="revealCell(i, j)"
          >
            <minesweeper-cell v-bind="cell" />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import MinesweeperCell from './MinesweeperCell'

const getRandomInt = max => {
  return Math.floor(Math.random() * Math.floor(max))
}

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
  },
  data () {
    return {
      board: []
    }
  },
  mounted () {
    this.populateBoard()
  },
  methods: {
    populateBoard () {
      for(let i=0; i<this.rows; i++) {
        let newRow = []
        for(let j=0; j<this.cols; j++) {
          newRow.push({
            revealed: false,
            isFlag: false,
            neighborFlags: 0
          })
        }
        this.board.push(newRow)
      }
      this.placeFlags()
      this.populateNeighbors()
    },
    placeFlags () {
      for(let i=0; i<this.flags; i++) {
        const row = getRandomInt(this.rows)
        const col = getRandomInt(this.cols)
        const cell = this.board[row][col]
        if (!cell.isFlag) {
          cell.isFlag = true
        } else {
          i -= 1
        }
      }
    },
    populateNeighbors () {
      for(let i=0; i<this.rows; i++) {
        for(let j=0; j<this.cols; j++) {
          // find neighbors of this cell
          const cell = this.board[i][j]
          for(let ii=-1; ii<2; ii++) {
            for(let jj=-1; jj<2; jj++) {
              const row = this.board[i + ii]
              if (row && row[j + jj] && row[j + jj].isFlag) {
                cell.neighborFlags += 1
              }
            }
          }
        }
      }
      return
    },
    revealCell (row, col) {
      this.board[row][col].revealed = true
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
