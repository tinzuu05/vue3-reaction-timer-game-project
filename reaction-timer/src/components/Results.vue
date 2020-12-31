<template>
<p>Reaction Time:{{ score }} ms</p>
<p class="rank"> {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 350) {
            this.rank = "Ninja Fingers"
        } else if (this.score < 700) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Snail Pace...'
        }
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    font-weight: bold;
    color: #41584b;
}

</style>