<template>
    <div>
        <base-button :class="checkIfClicked('Saved')" @click="showSavedBookmarksTab"
            >Saved</base-button
        >
        <base-button :class="checkIfClicked('New')" @click="showNewBookmarkTab"
            >New</base-button
        >
    </div>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
    props: {
        activeButton: String
    },
    emits: ["event-show-saved-bookmarks", "event-show-new-bookmark"],
    components: {
        BaseButton
    },
    methods: {
        checkIfClicked(item) {
            return { active: item === this.activeButton };
        },
        showSavedBookmarksTab() {
            this.$emit("event-show-saved-bookmarks");
        },
        showNewBookmarkTab() {
            this.$emit("event-show-new-bookmark");
        }
    }
};
</script>

<style scoped>
.active {
    background-color: #12232e;
    color: white;
}
</style>
