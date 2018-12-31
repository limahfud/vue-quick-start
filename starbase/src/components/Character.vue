<template>
    <article class="message is-success">
        <div class="message-header">
            <p>{{ character.name }}</p>
            <button class="delete" aria-label="delete"></button>
        </div>
        <div class="message-body">
            <p>Height: {{ character.height }}</p>
            <p>Mass: {{ character.mass }}</p>
            <p>Birth Year: {{ character.birth_year }}</p>
        </div>
    </article>

</template>


<script>
export default {
    data() {
        return {
            character : {}
        }
    },
    props : ['id'],
    methods : {
        fetchCharacter(id) {
            fetch(`http://swapi.co/api/people/${id}`, {
                method: 'GET'
            }).then(response => response.json())
            .then(json => this.character = json)
        }
    },
    created() {
        this.fetchCharacter(this.id)
    }
}
</script>

