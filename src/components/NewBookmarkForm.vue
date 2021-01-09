<template>
    <div class="new-input-form">
        <input type="text" placeholder="Title" v-model="bookmarkItemTitle" />
        <textarea
            placeholder="Description"
            v-model="bookmarkItemDescription"
        ></textarea>
        <input type="text" placeholder="Link" v-model="bookmarkItemLink" />

        <base-button class="save-button" @click="saveNewBookmark">
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
    computed: {
        bookmarkItemLinkCleaned() {
            if (this.bookmarkItemLink) {
                if (this.bookmarkItemLink.startsWith("http"))
                    return this.bookmarkItemLink;
                else return "https://" + this.bookmarkItemLink;
            }
            return "";
        }
    },
    methods: {
        saveNewBookmark() {
            const UID = generateID();
            let newBookmarkItemObject = {
                id: UID,
                bookmarkItemTitle: this.bookmarkItemTitle,
                bookmarkItemDescription: this.bookmarkItemDescription,
                bookmarkItemLink: this.bookmarkItemLinkCleaned
            };

            this.$emit("event-new-bookmark", newBookmarkItemObject);
        }
    }
};
</script>

<style scoped>
.new-input-form {
    background-color: white;
    border: 1px solid #12232e;
    width: 40%;
    margin: 0 auto;
    padding: 1rem 3rem;
    border-radius: 10px;
}

input {
    width: 100%;
    display: block;
    margin: 0 auto;
    height: 2rem;
    border: 1px solid black;
    border-radius: 5px;
    padding: 0 1rem;
}

textarea {
    width: 100%;
    height: 5rem;
    border: 1px solid black;
    border-radius: 5px;
    padding: 1rem 1rem;
    resize: none;
}

input,
textarea {
    margin-top: 2rem;
}

.save-button {
    margin-top: 2rem;
}
</style>
