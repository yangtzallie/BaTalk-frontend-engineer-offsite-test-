<template>

    <div id="tag">
        <button class="tagbutton" :class="tag.name===activatedTag?'activate':''" v-for="tag in tags" v-bind:key="tag.name" v-on:click="TagClick(tag.name)">{{tag.name}}</button>
       
    </div>
</template>


<script>
export default {
    name: 'tag',
    
    data: ()=>({
        tags: [],
        activatedTag:''
    }),
    methods: {
        sendMessageToParent(tagname){
            this.$root.$emit('mesg from tag',tagname)
        },
        TagClick(tagname){
            this.activatedTag=tagname
        },
        getTag(search=""){ 
            fetch(`https://api.stackexchange.com/2.3/tags?order=desc&sort=popular&site=stackoverflow${search?"&inname="+search:""}`).then(
                res=>res.json()
            ).then(json=>{
                this.tags=json.items.slice(0,10);
                this.activatedTag=this.tags[0].name;
            })
        },
        registerEvent(){
            this.$root.$on('msg from searchbar',(search)=>{this.getTag(search)})
        }
    },
    watch: {
        activatedTag: function(newActivated){
            this.sendMessageToParent(newActivated);
        }
    },
    mounted: function(){
        this.getTag()
        this.registerEvent()
    }
}
</script>

<style scoped>
#tag{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    
}
.tagbutton{
     margin: 3px;
     border-radius: 6px;
     border: 2px solid rgba(182, 216, 228, 1);
     padding: 4px;
     background: white;
}
.activate {
    background:rgba(182, 216, 228, 1);
}


</style>