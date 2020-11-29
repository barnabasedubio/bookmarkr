<template>
    <ul>
        <li v-for="item in bookmarkItems" :key="item.id">
            <bookmark-item :bookmark-item="item"></bookmark-item>
        </li>
    </ul>
</template>

<script>
    import BookmarkItem from "./BookmarkItem.vue"
    export default {
        props: {
            bookmarkItems: Array
        },
        components: {
            BookmarkItem
        }
    }
</script>

<style scoped>

</style>