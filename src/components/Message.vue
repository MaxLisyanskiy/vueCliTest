<template>
    <div class="message">
        <p>{{message}}</p>
    </div>
</template>

<script>
export default {
    props: {
        message: {
            type: String,
            reguiered: true
        }
    }
}
</script>

<style lang="scss" scoped>
.message {
    margin: 20px;
    text-align: center;
}
p {
    color: rgb(206, 35, 35);
}
</style>