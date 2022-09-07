<template>
  <div>
    <button @click="roll_number">Click To Roll</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      score: [{
        loss: undefined,
        wins: undefined
      }]
    }
  },
  methods: {
    roll_number () {
      axios
        .request({
          url: 'http://www.randomnumberapi.com/api/v1.0/randomnumber'
        })
        .then((res) => {
          this.rolled_number = res
          if (this.rolled_number < 50) {
            this.loss = this.loss + 1
          } else {
            this.wins = this.wins + 1
          }
        })
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
