<template>
    <div class="card p-2">
        <div class="card-body">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: ["quotes"]
};
</script>

<style lang="scss">

.card {
    cursor: pointer;
    &:hover {
        background-color: #ffe2e2;
    }
}
</style>
