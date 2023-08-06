<script setup>
import { computed, onMounted, ref } from 'vue'

const countriesList = ref([]);

const fetchCountries = async () => {
    const response = await fetch(`../countries.json`);
    const data = await response.json();
    countriesList.value = data;
}

onMounted(() => {
    fetchCountries();
})

</script>

<template>
    <div class="container">
        <!-- Bootstrap row wrapper div -->
        <div class="row">
            <!-- Countries List (Bootstrap column) -->
            <div v-if="countriesList.length > 0" class="col-5" style="max-height: 90vh; overflow: scroll">
                <router-link v-for="country in countriesList" class="country-item"
                    :to="{ name: 'details', params: { alpha3Code: country.alpha3Code } }">
                    <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`">
                    <p> {{ country.name.common }}</p>
                </router-link>>
            </div>
            <div class="col-7">
                <router-view></router-view>
            </div>
        </div>
    </div>
</template>

<style></style>