<template>
    <div>
        <input type="text" placeholder="title" v-model="bookmarkItemTitle" />
        <input
            type="text"
            placeholder="description"
            v-model="bookmarkItemDescription"
        />
        <input type="text" placeholder="link" v-model="bookmarkItemLink" />
        <base-button @click="saveNewBookmark">
            Save
        </base-button>
    </div>
</template>

<script>
import generateID from "../tools/generateID.js"
export default {
    emits: ["event-new-bookmark"],
    data() {
        return {
            bookmarkItemTitle: "",
            bookmarkItemDescription: "",
            bookmarkItemLink: ""
        };
    },
    methods: {
        saveNewBookmark() {
            const UID = generateID();
            let newBookmarkItemObject = {
                id: UID,
                bookmarkItemTitle: this.bookmarkItemTitle,
                bookmarkItemDescription: this.bookmarkItemDescription,
                bookmarkItemLink: this.bookmarkItemLink
            };

            this.$emit("event-new-bookmark", newBookmarkItemObject);
        }
    }
};
</script>

<style scoped></style>
