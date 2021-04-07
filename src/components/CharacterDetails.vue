<template>
    <section>
        <h3>{{character.name}}</h3>
        <p>Status: {{character.status}}</p>
        <p>Origin: {{character.origin.name}}</p>
    </section>
</template>

<script>
export default {
    name: 'character-details',
    props: ['character']

}
</script>

<style scoped>

</style>