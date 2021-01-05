<template>
    <the-header></the-header>

    <div class="content">
        <menu-bar
            @event-show-saved-bookmarks="setActiveTab('bookmark-item-list')"
            @event-show-new-bookmark="setActiveTab('new-bookmark-form')"
        ></menu-bar>

        <new-bookmark-form
            v-if="selectedComponent === 'new-bookmark-form'"
            @event-new-bookmark="addNewBookmarkItem"
        ></new-bookmark-form>

        <bookmark-item-list
            v-if="selectedComponent === 'bookmark-item-list'"
            :bookmark-items="bookMarkList"
        ></bookmark-item-list>
    </div>

    <!-- <the-footer></the-footer> -->
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
// import TheFooter from "./components/TheFooter.vue";
import MenuBar from "./components/MenuBar.vue";
import BookmarkItemList from "./components/BookmarkItemList.vue";
import NewBookmarkForm from "./components/NewBookmarkForm.vue";
export default {
    name: "App",
    components: {
        TheHeader,
        // TheFooter,
        MenuBar,
        BookmarkItemList,
        NewBookmarkForm
    },
    data() {
        return {
            bookMarkList: [],
            selectedComponent: "bookmark-item-list"
        };
    },
    methods: {
        addNewBookmarkItem(newBookmarkItemObject) {
            console.log(newBookmarkItemObject);
            this.bookMarkList.push(newBookmarkItemObject);
            this.selectedComponent = "bookmark-item-list";
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
}

html,
body {
    height: 100%;
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
    border: 1px solid red;
    position: relative;
    top: 7%;
}
</style>
