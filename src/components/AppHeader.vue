<script>
export default {
    name: "AppHeader"
}
</script>

<template>
    <header>
        <div id="boxHeader">
            <img src="../../public/Yugioh_anime_logo.webp" alt="logo">
            <h1>Yu-Gi-Oh Api</h1>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use '../style.scss' as *;

#boxHeader {
    @include flex(row, start, center);
    height: 4rem;
    padding: 1em;

    img {
        height: 90%;
    }

    h1 {
        font-weight: 100;
    }
}
</style>