<script>
import { store } from '../data/store'
export default {
    name: "AppMain",
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <main>
        <div class="container">
            <div class="mainHead">
                <h4>Found 39 cards</h4>
            </div>
            <div class="boxMain">
                <div v-for="element, i in store.cards" class="card">
                    <div class="content">
                        <img :src="element.card_images[0].image_url" :alt="element.name">
                    </div>
                    <div class="title">
                        <h5>{{ element.name }}</h5>
                    </div>
                    <div class="type">
                        <small>{{ element.type }}</small>
                    </div>
                </div>
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
                text-align: center;
                background-color: #d48f38;
                line-height: 1.5rem;

                img {
                    width: 100%;
                }

                .title {
                    color: white;
                }
            }
        }
    }
}
</style>