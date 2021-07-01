<template>
    <div id="searchComponent">
        <input class="searchbar" type="text" v-model="searchbar" placeholder="Tag"/> 
        <button class="searchbutton" v-on:click="search">Search</button>
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

<style scoped>
#searchComponent{
    display: flex;
    flex-direction: row;
}

.searchbar{
    flex-grow: 2;
    border-radius: 6px;
    border-top-right-radius: 0px;
    border-bottom-right-radius: 0px;
    border: 2px solid rgba(182, 216, 228, 1);
    height: 30px;

}
.searchbutton{
    border-radius: 6px;
    border-top-left-radius: 0px;
    border-bottom-left-radius: 0px;
    background:rgba(182, 216, 228, 1);
    border: 2px solid rgba(204, 217, 222, 1);
}

</style>