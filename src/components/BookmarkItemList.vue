<template>
    <ul v-if="bookmarkItems.length">
        <li v-for="item in bookmarkItems" :key="item.id">
            <bookmark-item :bookmark-item="item"></bookmark-item>
        </li>
    </ul>
    <p class="empty-bookmark-list-text" v-else>Your bookmark list is empty. Add a new bookmark!</p>
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
.empty-bookmark-list-text {
    position: relative;
    top: 10rem;
}
</style>