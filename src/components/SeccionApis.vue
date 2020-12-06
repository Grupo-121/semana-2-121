<template>

</template>

<script>

export default {
    name: 'SeccionApis',
    data(){
        return{
            movies: null
        }
    },
    mounted(){
        fetch('http://www.omdbapi.com/?t=guardianes&apikey=ec274c35')
        .then(response => {
            (this.info = response.data.Search) 
            console.log(this.info.data)
            })
    }
}
</script>
