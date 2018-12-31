<template>
    <div>
        <div>
            Type : {{ type }}
        </div>

        <ul>
            <li v-for="(item, index) in items" v-bind:key="index">
                <article class="message" :class="{'is-primary' : type == 'planets'}">
                    <div class="message-header">
                        <p>{{ item.name }}</p>
                        <button class="delete" aria-label="delete"></button>
                    </div>
                    <div class="message-body" v-if="type == 'planets'">
                        <p>Rotation Period: {{ item.rotation_period }}</p>
                        <p>Diamerer: {{ item.diameter }}</p>
                        <p>Terrain: {{ item.terrain }}</p>
                    </div>
                    <div class="message-body" v-if="type == 'people'">
                        <p>Height: {{ item.height }}</p>
                        <p>Mass: {{ item.mass }}</p>
                        <p>Skin Color: {{ item.skin_color }}</p>
                    </div>
                </article>
            </li>
        </ul>
    </div>
</template>

<style>
article {
    max-width: 300px;
}
</style>


<script>
export default {
    data() {
        return {
            type : this.$route.params.type,
            items : []
        }
    },
    watch: {
        '$route' : 'fetchItems'
    },
    methods: {
        fetchItems() {
            this.type = this.$route.params.type

            this.items = []
            const initial_ids = [1, 21, 45]
            initial_ids.forEach( id => {
                fetch (`http://swapi.co/api/${this.type}/${id}`, {
                    method : 'GET'
                })
                .then( response => response.json())
                .then( json => this.items.push(json))
            })

        },
    
    }
}
</script>

