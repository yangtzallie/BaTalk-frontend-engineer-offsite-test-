<template>
    <!-- <div class="searchbar">
        <input v-model="message">

    </div> -->
    <div>
        <input type="text" v-model="searchbar" placeholder="Tag" /> 
        <button v-on:click="search">Search</button>
    </div>
</template>


<script>
export default {
    name: 'searchbar',
    props: {
        type: String
    }
}
</script>