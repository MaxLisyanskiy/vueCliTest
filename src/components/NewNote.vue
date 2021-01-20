<template>
    <div class="new-note">
        <label>New Title</label>
        <input v-model="note.title" type="text">
        <label>New Description</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">New note!</button>
    </div>
</template>

<style lang="scss" scoped>
.new-note {
    text-align: center;
    width: 50%;
    margin: 0 auto;
}
button {
    display: block;
    margin: 15px auto;
}
</style>

<script>
export default {
    props: {
        note: {
            type: Object,
            reguiered: true
        }
    },
    methods: {
        addNote() {
            this.$emit('addNewNote', this.note)
        }
    }
}
</script>