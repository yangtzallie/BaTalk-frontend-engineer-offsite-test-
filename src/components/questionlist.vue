<template>

    <div>
        <div v-for="question in questionlist" v-bind:key="question.id">
            <h1> {{question.name}}</h1>
            <div>
                <span>Score</span>
                <span>{{question.score}}</span>
            </div>
             <div>
                <span>Answers</span>
                <span>{{question.answer}}</span>
            </div>
             <div>
                <span>Viewed</span>
                <span>{{question.view}}</span>
            </div>
            <img alt="Vue logo" src="../assets/logo.png">
        
        <hr>
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
        questionlist: [
      { id: 1, name:'wer',score: 'a',answer:'b',view:'c' },
      { id: 2, name:'qer',score: 'a',answer:'b',view:'c' },
      { id: 3, name:'wqrewrge',score: 'a',answer:'b',view:'c' },
      { id: 4, name:'er',score: 'a',answer:'b',view:'c' },
      { id: 5, name:'ewqew',score: 'a',answer:'b',view:'c' },
      { id: 6, name:'eww',score: 'a',answer:'b',view:'c' },
      { id: 7, name:'ewqew',score: 'a',answer:'b',view:'c' },
      { id: 8, name:'ewqew',score: 'a',answer:'b',view:'c' },
      { id: 9, name:'ewqew',score: 'a',answer:'b',view:'c' },
      { id:10, name:'ewqew',score: 'a',answer:'b',view:'c' },

    ]
    })
}
</script>