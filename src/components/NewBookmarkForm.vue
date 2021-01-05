<template>
    <div class="new-input-form">
        <input type="text" placeholder="title" v-model="bookmarkItemTitle" />
        <textarea
            type="text"
            placeholder="description"
            v-model="bookmarkItemDescription"
        ></textarea>
        <input
            type="text"
            placeholder="link"
            v-model="bookmarkItemLink"
        />

        <base-button @click="saveNewBookmark">
            Save
        </base-button>
    </div>
</template>

<script>
import generateID from "../tools/generateID.js";
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

<style scoped>
input {
    width: 30%;
    display: block;
    margin: 0 auto;
    height: 2rem;
    border: 1px solid black;
    border-radius: 5px;
    padding: 0 1rem;
}

textarea {
    width: 30%;
    height: 5rem;
    border: 1px solid black;
    border-radius: 5px;
    padding: 1rem 1rem;
    resize: none;
}

input,textarea {
    margin-top: 2rem;
}
</style>
