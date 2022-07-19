<template>
{{searchBox}}
  
</template>

<script>
export default {
    name: "SearchBar",
    data (){
        return {
            value:"search for movies!"
        }
    }
}
</script>

<style scoped>
    input{
        height: 20px;
        width: 100%;
    }
</style>