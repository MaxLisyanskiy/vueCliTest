<template>
    <div class="notes">
        <div class="note" :class="{ full: !grid }" v-for="(note, index) in notes" :key="index">
            <div class="note-header">
                <p>{{note.title}}</p>
                <p style="cursor: pointer; color: #999999;" @click="removeNote(index)">x</p>
            </div>
            <div class="note-body">
                <p>{{note.descr}}</p>
                <span>{{note.date}}</span>
            </div>
        </div>
    </div>
</template> 

<style lang="scss">
.notes{
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}
.note {
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 10px;
    background-color: #fff;
    &.full{
        width: 100%;
    }
}
.note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1 {
        font-size: 25px;
    }
    p {
        font-weight: 600;
    }
    svg {
        cursor: pointer;
        margin-right: 10px;
        color: #999999;
        &.active{
            color: #2b008f;
        }
        &:last-child{
            margin-right: 0;
        }
    }
}
.note-body {
    p {
        margin: 10px 0;
        font-size: 16px;
    }
    span{
        font-size: 14px;
        color: #999999;
    }
}
</style>

<script>
export default {
    props: {
        notes: {
            type: Array,
            requierd: true
        },
        grid: {
            type: Boolean,
            requierd: true
        }
    },
    methods: {
        removeNote (index) {
            console.log(`Notes id ${index} removed`),
            this.$emit('remove', index)
        }
    }
}
</script>