<template>
    <div class="bookmark-item">
        <h3>{{ bookmarkItem.bookmarkItemTitle }}</h3>
        <p>{{ bookmarkItem.bookmarkItemDescription }}</p>
        <p>{{ bookmarkItem.bookmarkItemLink }}</p>
    </div>
</template>

<script>
export default {
    props: {
        bookmarkItem: Object
    }
};
</script>

<style scoped></style>
