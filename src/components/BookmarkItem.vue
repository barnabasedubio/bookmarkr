<template>
    <div class="bookmark-card">
        <div class="bookmark-item bookmark-title">
            <h2>{{ bookmarkItem.bookmarkItemTitle }}</h2>
            <span>
                <button class="deleteBookmarkButton" @click="deleteBookmark">
                    Delete
                </button>
            </span>
        </div>
        <div
            v-if="bookmarkItem.bookmarkItemDescription"
            class="bookmark-item bookmark-description"
        >
            <p>{{ bookmarkItem.bookmarkItemDescription }}</p>
        </div>
        <div class="bookmark-item bookmark-link">
            <a :href="bookmarkItem.bookmarkItemLink" target="_blank"
                >Visit link
                <img class="link-icon" src="../../assets/external-link.svg"
            /></a>
        </div>
    </div>
</template>

<script>
export default {
    emits: ["event-delete-bookmark"],
    props: {
        bookmarkItem: Object
    },
    methods: {
        deleteBookmark() {
            this.$emit("event-delete-bookmark", this.bookmarkItem.id);
        }
    }
};
</script>

<style scoped>
h2 {
    font-size: x-large;
}

a {
    text-decoration: none;
    color: #007cc7;
}

h2,
p {
    color: #12232e;
}

.bookmark-card {
    border: 1px solid #12232e;
    width: 40%;
    margin: 2rem auto;
    padding: 1rem;
    border-radius: 10px;
    background-color: white;
}

.bookmark-item {
    padding: 0.5rem 0;
    text-align: left;
}

.bookmark-title h2 {
    width: 85%;
    display: inline-block;
}

.bookmark-description {
    overflow-wrap: break-word;
}

.deleteBookmarkButton {
    padding: 0.4rem 1.2rem;
    position: relative;
    bottom: 0.25rem;
    left: 1.5rem;
    color: #12232e;
    background-color: transparent;
    border: 0;
}

.deleteBookmarkButton:hover {
    background-color: #12232e;
    color: white;
}

.link-icon {
    width: 15px;
    height: 15px;
    position: relative;
    top: 1px;
    left: 3px;
    /*
    https://stackoverflow.com/questions/22252472/how-to-change-the-color-of-an-svg-element/53336754#53336754
     */
    filter: invert(39%) sepia(50%) saturate(5628%) hue-rotate(182deg)
        brightness(89%) contrast(102%);
}
</style>
