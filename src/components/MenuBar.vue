<template>
    <div>
        <base-button @click="showSavedBookmarksTab">Saved</base-button>
        <base-button @click="showNewBookmarkTab">New</base-button>
    </div>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
    emits: ["event-show-saved-bookmarks", "event-show-new-bookmark"],
    components: {
        BaseButton
    },
    methods: {
        showSavedBookmarksTab() {
            this.$emit("event-show-saved-bookmarks");
        },
        showNewBookmarkTab() {
            this.$emit("event-show-new-bookmark");
        }
    }
};
</script>

<style scoped></style>
