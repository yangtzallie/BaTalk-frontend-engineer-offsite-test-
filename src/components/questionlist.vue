<template>
    <div class="scroll" @scroll="scroll" >
        <div class="questionlist">
            <div class="row question" v-for="question in questionlist" v-bind:key="question.id">
                <div class="col questionDetail">
                    <div>
                        <a class="questionTitle" :href="question.link"  target=”_blank” >{{question.title}}</a>
                    </div>
                    <div class="row questionrecord">
                        <div class="col centerAlign">
                            <div class="red">Score</div>
                            <div :class="question.score<0?'scoreHightlight':''">{{question.score}}</div>
                        </div>
                        <div class="col centerAlign">
                            <div class="red">Answers</div>
                            <div :class="question.answer_count===0?'':question.is_answered===true?'answerAcceptHightlight':'answerUnAcceptHightlight'">{{question.answer_count}}</div>
                        </div>
                        <div class="col centerAlign">
                            <div class="red">Viewed</div>
                            <div>{{question.view_count}}</div>
                        </div>
                    </div>
                </div>
                <div class="col centerAlign owner">
                    <img alt="owner pic" :src="question.owner.profile_image">
                    <div>{{question.owner.display_name}}</div>
                </div>

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
        getQuestion(){ 
            if(this.loading==false){
                this.loading=true
                fetch(`https://api.stackexchange.com/2.3/questions?page=${this.page}&pagesize=20&order=desc&sort=activity&site=stackoverflow&tagged=${this.tag}`).then(
                    res=>res.json()
                ).then(json=>{
                    this.questionlist=this.questionlist.concat(json.items)
                    this.loading=false
                })
            }
        },
        rgsEvent(){
            this.$root.$on('mesg from tag',(tagname)=>{
                this.page=1;
                this.questionlist=[];
                this.tag=tagname;
                this.getQuestion();
            });
            
        },
        loadmore(){
            if (this.bottom === true){
                this.page=this.page+1;
                this.getQuestion()
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
    mounted: function() { 
        this.rgsEvent()
    }
}
</script>



<style scoped>
.row{
    display: flex;
    flex-direction: row;
}
.col{
    display: flex;
    flex-direction: column;
}
.centerAlign{
    align-items: center;
}
.red{
    color: rgb(147,67,76);
}
img{
    width: 100px;
    height: 100px;
    object-fit: cover;
    border-radius: 50%;
    border:rgb(228, 228, 228) solid 0.5px;
}
.owner{
    width: 100px;
}
.owner div{
    text-align: center;
}
.questionDetail{
    flex-grow: 1;

}
.questionDetail>div:first-child{
    margin-bottom: 8px;
}
.questionrecord{
    justify-content: space-evenly;
}
.question{
    display: flex;
    justify-content: space-between;
    border-bottom:rgb(228, 228, 228) solid 0.5px;
    padding: 4px;
}
.scoreHightlight{
    color: red;
}
.answerAcceptHightlight{
    color:white;
    border:rgb(55, 124, 39) solid 1px;
    padding-left: 25px;
    padding-right: 25px;
    background:rgb(55, 124, 39);

}
.answerUnAcceptHightlight{
    color:rgb(55, 124, 39);
    border: rgb(55, 124, 39) solid 1px;

    padding-left: 25px;
    padding-right: 25px;
}
.questionTitle{
    color: black;
    text-decoration: none;
}
.scroll{
    max-height: 100%;
    overflow: scroll;
}
</style>