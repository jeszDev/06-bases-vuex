<template>
    <h1>Counter - Vuex</h1>
    <!-- <h2>Direct access: {{ $store.state.count }}</h2> -->
    <h2>Direct access: {{ $store.state.counter.count }}</h2>
    <h3>Computed: {{ countComputed }}</h3>

    <button @click="increment">+1</button>
    <button @click="incrementBy">+5</button>
    <button @click="incrementRandomInt" :disabled="isLoading">Random</button>

    <h2>mapState</h2>
    <h3>mapState: {{ count }}</h3>
    <h3>lastMutation: {{ lastMutation }}</h3>


    <h2>Getters</h2>
    <h3>Direct getter: {{ $store.getters['counter/squareCount'] }}</h3>
</template>

<script>
import { mapState, mapActions } from "vuex";
export default {

    // computed: mapState(['count'])

    computed: {
        countComputed() {
            // return this.$store.state.count
            return this.$store.state.counter.count
        },
        // ...mapState(['count', 'lastMutation', 'isLoading'])
        // ...mapState({
        //     count: state => state.count,
        //     lastMutation: state => state.lastMutation
        // })
        ...mapState('counter', ['count', 'lastMutation', 'isLoading'])
    },

    methods: {
        increment() {
            // this.$store.commit('increment')
            this.$store.commit('counter/increment')
        },
        incrementBy() {
            // this.$store.commit('incrementBy', 5)
            //this.randomIn() //llamando funcion de las mapActions

            this.$store.commit('counter/incrementBy', 5)
        },
        // incrementRandomInt() {
        //     this.$store.dispatch( 'incrementRandomInt' )
        // }
        // ...mapActions(['incrementRandomInt'])
        ...mapActions('counter', ['incrementRandomInt'])
    }


}
</script>
