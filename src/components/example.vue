<template>
<div>{{ item.title }}</div>
</template>
<script>
export default {
    asyncData ({ store, route }) {
        // 路由组件中可能出现该方法
        // 该函数将在组件实例化之前调用，所以不能访问this
        // 触发 action 后，会返回 Promise
        return store.dispatch('fetchItem', route.params.id)
    },
    computed: {
        // 从 store 的 state 对象中的获取 item。
        item () {
            return this.$store.state.items[this.$route.params.id]
        }
    }
}
</script>
