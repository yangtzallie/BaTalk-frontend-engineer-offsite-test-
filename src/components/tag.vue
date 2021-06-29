<template>

    <div>
        <button v-for="tag in tags" v-bind:key="tag.id" v-on:click="TagClick">{{tag.text}}</button>
       
    </div>
</template>


<script>
export default {
    name: 'tag',
    
    data: ()=>({
        tags: [
      { id: 1, text: 'a' },
      { id: 2, text: 'b' },
      { id: 3, text: 'c' },
      { id: 4, text: 'y' },
      { id: 5, text: 't' },
      { id: 6, text: 'r' },
      { id: 7, text: 'e' },
      { id: 8, text: 'w' },
      { id: 9, text: 'q' },
      { id:10, text: 'p' }

    ]
    })
}
</script>