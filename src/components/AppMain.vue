<script>
export default {
    name: "AppMain"
}
</script>

<template>
    <main>
        <div class="container">
            <div class="mainHead">
                <h4>Found 39 cards</h4>
            </div>
            <div class="boxMain">
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
                <div class="card"></div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use '../style.scss' as *;

main {
    background-color: #d48f38;
    padding: 3.5rem;

    .container {
        width: 1080px;
        margin: 0 auto;
        padding: 3rem;
        background-color: white;

        h4 {
            background-color: #212529;
            color: white;
            padding: 1rem;
        }

        .boxMain {
            @include flex(row, space-between, center, wrap);
            gap: 1em;

            .card {
                width: calc(100% / 5 - 1em);
                height: 388px;
                background-color: red;
            }
        }
    }
}
</style>