<template>
    <div class="home">
        <h2>Strona główna</h2>
    </div>
</template>

<script>
export default {
    name: 'HomeView',
    data() {
        return {
            email: "",
            password: "",
            error: "",
        };
    },
    methods: {
    },
};
</script>

<style scoped>
.login {
    max-width: 300px;
    margin: 0 auto;
    padding: 1em;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.login div {
    margin-bottom: 1em;
}

.login label {
    display: block;
    margin-bottom: 0.5em;
}

.login input {
    width: 100%;
    padding: 0.5em;
    box-sizing: border-box;
}
</style>