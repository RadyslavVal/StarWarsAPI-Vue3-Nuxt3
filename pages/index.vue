<script setup>

/* const { data } = await useFetch('https://swapi.dev/api/films/')
console.log(data.value.results) */



definePageMeta({
    key: route => route.fullPath
})
</script>


<template>
    <div>
        <ul>
            <!-- <li v-if="data">
                {{ data }}
            </li> -->
        </ul>
    </div>
</template>

