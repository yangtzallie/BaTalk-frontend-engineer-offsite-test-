<template>
    <div class="scroll" @scroll="scroll" style="height: 90vh; overflow:auto">
    <div>
        <div v-for="question in questionlist" v-bind:key="question.id">
            <h1> {{question.title}}</h1>
            <div>
                <span>Score</span>
                <span>{{question.score}}</span>
            </div>
             <div>
                <span>Answers</span>
                <span>{{question.answer_count}}</span>
            </div>
             <div>
                <span>Viewed</span>
                <span>{{question.view_count}}</span>
            </div>
            <img alt="owner pic" :src="question.owner.profile_image">
            <span>{{question.owner.display_name}}</span>
        
        <hr>
        </div>
       
        </div>
        
    </div>
</template>


<script>
export default {
    name: 'questionlist',
    props: {
        type: String
    },
    data: ()=>({
        questionlist: [],
        bottom: false,
        loading:false,
        tag:"",
        page:1
    }),
    methods: { 
        getTag(tag='',page=1){ 
            if(this.loading==false){
                this.loading=true
                fetch(`https://api.stackexchange.com/2.3/questions?page=${page}&pagesize=20&order=desc&sort=activity&site=stackoverflow&tagged=${tag}`).then(
                    res=>res.json()
                ).then(json=>{
                    this.questionlist=this.questionlist.concat(json.items)
                    this.loading=false
                })
            }
        },
        rgsEvent(){
            this.$root.$on('mesg from tag',(tagname)=>{this.getTag(tagname,1);this.tag=tagname});
            
        },
        loadmore(){
            if (this.bottom === true){
                this.page=this.page+1;
                this.getTag(this.tag,this.page)
                this.bottom=false
            }
        },
        scroll(e){
            const {target} = e;
            if (Math.ceil(target.scrollTop) >=target.scrollHeight - target.offsetHeight) {
                this.bottom = true;
                this.loadmore()
            }
        }
        
    },
    mounted: function() {  this.rgsEvent()}
}
</script>

<style lang="less" scoped>

</style>


questionlist.func()