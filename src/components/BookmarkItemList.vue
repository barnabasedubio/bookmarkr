<template>
    <ul v-if="bookmarkItems.length">
        <li v-for="item in bookmarkItems" :key="item.id">
            <bookmark-item :bookmark-item="item"></bookmark-item>
        </li>
    </ul>
    <h2 v-else>Add a Bookmark</h2>
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