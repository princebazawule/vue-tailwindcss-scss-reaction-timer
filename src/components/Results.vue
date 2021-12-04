<template>
    <div class="score my-8">
        <p class="text-2xl">
            <span class="font-bold">Your Score: </span> 
            <span class="italic"> {{ score }} ms</span>
        </p>
        <p 
            class="my-4 py-4 ring-2 max-w-sm mx-auto rounded-full"
            :class="[((this.score <= 500) ? 'ring-green-200' : ''), ((this.score > 500 && this.score < 900) ? 'ring-gray-200' : ''), ((this.score >= 900) ? 'ring-red-200' : '')]"
        >{{ rank }}</p>
    </div>
</template>

<script>
export default {
    name: 'Results',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 500) {
            this.rank = 'Wooo trigger fingers!  🎉'
        } else if (this.score >= 500 && this.score <= 900) {
            this.rank = 'Yep, keep doing ya thang! 🦾'
        } else {
            this.rank = 'Need practice, mate! 😭'
        }
    },
}
</script>

<style>

</style>