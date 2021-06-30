<template>
    <div>
        <input type="text" v-model="searchbar" placeholder="Tag"/> 
        <button v-on:click="search">Search</button>
    </div>
</template>


<script>
export default {
    name: 'searchbar',
    data: ()=>({
        searchbar: '',
    }),
    methods: {
        search(){
            console.log('this is search')
        },
        sendMessageToParent(search){
            this.$root.$emit('msg from searchbar', search)
        }
    },
    watch: {
        searchbar(newsearch){
            this.sendMessageToParent(newsearch)
        }
    }
}
</script>