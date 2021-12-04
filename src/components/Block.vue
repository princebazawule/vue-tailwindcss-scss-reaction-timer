<template>
    <div 
        v-if="showBlock"
        @click="stopTimer"
        class="bg-green-500 text-white h-40 w-60 rounded-lg mx-auto flex flex-col justify-center items-center cursor-pointer"
    >
      click me
    </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
      startTimer() {
          this.timer = setInterval(() => {
              this.reactionTime += 10
          }, 10)
      },
      stopTimer() {
          clearInterval(this.timer)
          console.log('reaction time:', this.reactionTime)
          this.$emit('end', this.reactionTime)
      }
    },
}
</script>
    
<style>

</style>