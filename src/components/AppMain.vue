<script>
import axios from 'axios';
import { store } from '../data/store'
export default {
    name: "AppMain",
    data() {
        return {
            store,
            arrayArchetype: [],
            currentArchetype: null
        }
    },

}
</script>

<template>
    <main>
        <select @change="searhType" v-model="currentArchetype">
            <option v-for="cardType in store.cards" :value="cardType.archetype">
                {{ cardType.archetype }}
            </option>
        </select>
        <div class="container">
            <div class="mainHead">
                <h4>Found 40 cards</h4>
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
                        <small>{{ element.archetype }}</small>
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

    select {
        margin-bottom: 2rem;
        padding: 1em;
        border: 0;
        border-radius: 1em;
    }

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