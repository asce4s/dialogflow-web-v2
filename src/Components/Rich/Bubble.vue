<template>
    <div class="bubble" tabindex="0" :class="{'me': me, 'loading': loading}">{{text}}</div>
</template>

<style lang="sass" scoped>
.bubble
    padding: 12px
    border-radius: 40px
    color: var(--text)
    border: 1px solid var(--border)
    display: inline-block
    position: relative
    background-color: var(--background)
    min-width: 26px

    &::before
        content: var(--left-bubble)
        position: absolute
        left: 0
        top: 0
        margin-top: -9px
        margin-left: -1px

    &.me
        background-color: var(--text)
        border: 1px solid var(--text)
        color: var(--component-background)

        &::before
            content: ''

        &::after
            content: var(--right-bubble)
            position: absolute
            right: 0
            top: 0
            margin-top: -9px
            margin-right: -1px

    &.loading
        height: 16px
        animation: loading .8s ease infinite

@keyframes loading
    0%
        opacity: 0
    50%
        opacity: 1
    100%
        opacity: 0
</style>

<script>
export default {
    name: 'Bubble',
    props: {
        text: {
            type: String,
            required: false,
            default: ''
        },
        me: {
            type: Boolean
        },
        loading: {
            type: Boolean
        }
    }
}
</script>