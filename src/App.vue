<template>
    <the-header></the-header>
    <menu-bar></menu-bar>
    <new-bookmark-form
        @event-new-bookmark="addNewBookmarkItem"
    ></new-bookmark-form>
    <bookmark-item-list :bookmark-items="bookMarkList"></bookmark-item-list>
    <the-footer></the-footer>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";
import MenuBar from "./components/MenuBar.vue";
import BookmarkItemList from "./components/BookmarkItemList.vue";
import NewBookmarkForm from "./components/NewBookmarkForm.vue";
export default {
    name: "App",
    components: {
        TheHeader,
        TheFooter,
        MenuBar,
        BookmarkItemList,
        NewBookmarkForm
    },
    data() {
        return {
            bookMarkList: []
        };
    },
    methods: {
        addNewBookmarkItem(newBookmarkItemObject) {
            console.log(newBookmarkItemObject);
            this.bookMarkList.push(newBookmarkItemObject);
        }
    }
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
