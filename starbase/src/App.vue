<template>
<div id="app">
    <h3>{{ title }}</h3>

    <Character v-for="(character_id, key) in initial_ids" v-bind:id="character_id" v-bind:key="key"/>

    <button class="button is-primary" @click="generateRandom()">Generate Random</button>
    
</div>
</template>

<script>
import Character from './components/Character.vue'

export default {
    name: 'app',
    data() {
        return {
            title: 'Generate Your Team',
            initial_ids: [1,11,21]
        }
    },
    components : { Character },
    methods : {
        generateRandom() {
            this.initial_ids.push(this.initial_ids.length + 1)
        }
    }
}
</script>
