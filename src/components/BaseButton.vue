<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
export default {};
</script>

<style scoped>
button {
    min-width: 8rem;
    padding: 0.5rem 1.5rem;
    margin: 1rem 2rem;
    border: 1px solid #12232e;
    border-radius: 5px;
    color: #12232e;
    background-color: transparent;
}

button:hover {
    color: white;
    background-color: #12232e;
}
</style>
