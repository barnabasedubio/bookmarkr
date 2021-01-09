<template>
    <the-header></the-header>

    <div class="content">
        <menu-bar
            @event-show-saved-bookmarks="setActiveTab('bookmark-item-list')"
            @event-show-new-bookmark="setActiveTab('new-bookmark-form')"
            :activeButton="activeButton"
        ></menu-bar>

        <new-bookmark-form
            @event-new-bookmark="addBookmark"
            v-if="selectedComponent === 'new-bookmark-form'"
        ></new-bookmark-form>

        <bookmark-item-list
            @event-delete-bookmark="deleteBookmark"
            v-if="selectedComponent === 'bookmark-item-list'"
            :bookmark-items="bookmarks"
        ></bookmark-item-list>
    </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import MenuBar from "./components/MenuBar.vue";
import BookmarkItemList from "./components/BookmarkItemList.vue";
import NewBookmarkForm from "./components/NewBookmarkForm.vue";
export default {
    name: "App",
    components: {
        TheHeader,
        MenuBar,
        BookmarkItemList,
        NewBookmarkForm
    },
    data() {
        return {
            bookmarks: [],
            selectedComponent: "bookmark-item-list"
        };
    },
    computed: {
        activeButton() {
            if (this.selectedComponent === "bookmark-item-list") {
                return "Saved";
            } else if (this.selectedComponent === "new-bookmark-form") {
                return "New";
            }

            return "";
        }
    },
    methods: {
        addBookmark(newBookmarkItemObject) {
            if (!newBookmarkItemObject.bookmarkItemTitle) {
                alert("Please provide a title for your bookmark.");
                return;
            }
            if (!newBookmarkItemObject.bookmarkItemLink) {
                alert("Please provide an link for your bookmark.");
                return;
            }
            this.bookmarks.unshift(newBookmarkItemObject);
            this.selectedComponent = "bookmark-item-list";
        },
        deleteBookmark(bookmarkId) {
            this.bookmarks = this.bookmarks.filter(
                bookmark => bookmark.id != bookmarkId
            );
        },
        setActiveTab(activeTab) {
            this.selectedComponent = activeTab;
        }
    }
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

h1,
h2,
h3,
h4,
h5,
h6,
p,
a,
button {
    font-family: "Trebuchet MS";
}

html {
    background-color: #eefbfb;
}

html,
body {
    height: 100%;
    min-height: 100%;
}

#app {
    height: inherit;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.content {
    position: relative;
    top: 7%;
    padding-bottom: 2rem;
}

button {
    cursor: pointer;
    font-size: large;
    border-radius: 5px;
    transition: color 0.1s linear, background-color 0.5s;
}
</style>
