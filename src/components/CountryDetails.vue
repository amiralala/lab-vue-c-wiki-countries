<script setup>
import {ref, onMounted, watch} from 'vue'
import {useRoute} from 'vue-router'

const route=useRoute();

const country = ref({});

const fetchCountry = async () => {
    const url = `https://ih-countries-api.herokuapp.com/countries/${route.params.alpha3Code}`;
    console.log("url "+url);
    const response = await fetch(url);
    const data = await response.json();
    country.value = data;
    console.log(country.value.alpha2Code);
}

onMounted(() => {
    fetchCountry();
})

watch(
    () => route.params.alpha3Code,
    () => {fetchCountry()}
)


</script>

<template>
    <h1>Country Details</h1>
    <h2>{{ route.params.alpha3Code }}</h2>
    <div v-if="country.alpha2Code">
        <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`">
    </div>
</template>

<style></style>