<template>
    <ul v-if="bookmarkItems.length">
        <li v-for="item in bookmarkItems" :key="item.id">
            <bookmark-item
                :bookmark-item="item"
                @event-delete-bookmark="deleteBookmark"
            ></bookmark-item>
        </li>
    </ul>
    <h4 class="empty-bookmark-list-text" v-else>
        Your bookmark list is empty. Add a new bookmark!
    </h4>
</template>

<script>
import BookmarkItem from "./BookmarkItem.vue";
export default {
    emits: ["event-delete-bookmark"],
    props: {
        bookmarkItems: Array
    },
    components: {
        BookmarkItem
    },
    methods: {
        deleteBookmark(bookmarkId) {
            // re-emitting deletebookmark from the bookmarkitem compoent in order
            // for App.vue to handle event
            this.$emit("event-delete-bookmark", bookmarkId);
        }
    }
};
</script>

<style scoped>
.empty-bookmark-list-text {
    position: relative;
    top: 10rem;
}
</style>
