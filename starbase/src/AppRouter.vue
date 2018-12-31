<template>
<div id="app">
    <h3>{{ title }}</h3>

    <ul>
        <li>
            <router-link to="/data/people">Meet the Characters</router-link>
            <router-link to="/data/planets">Exploret the Planets</router-link>
        </li>
    </ul>
    <router-view></router-view>
    
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
