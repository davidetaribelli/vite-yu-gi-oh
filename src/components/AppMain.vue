<script>
import axios from 'axios';
import { store } from '../data/store'
export default {
    name: "AppMain",
    data() {
        return {
            store,
            currentArchetypes: null,
            counterCard: 0
        }
    },
    methods: {
        searchArchetypes() {
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.currentArchetypes}`).then(r => {
                this.store.cards = r.data.data
                this.counterCard = this.store.cards.length
            })
        }
    }
}
</script>

<template>
    <main>
        <select @change="searchArchetypes" v-model="currentArchetypes">
            <option v-for="cardType in store.archetypes" :value="cardType.archetype_name">
                {{ cardType.archetype_name }}
            </option>
        </select>
        <div class="container">
            <div class="mainHead">
                <h4>Found {{ counterCard }} cards</h4>
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
            @include flex(row, start, center, wrap);
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