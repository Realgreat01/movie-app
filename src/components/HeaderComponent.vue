<template>
<h3></h3>

</template>
<script>
import SearchBar from "@/components/SearchBar";
export default {
    name: "HeaderComponent",
    data(){
        return{
            searchToggle: false
        }
    },
    components: {
    }
} 
</script>

<style scoped>
    nav{
        display:flex;
        height: 30px;
        justify-content: space-between;
        align-items: center;
    }
    ul{
        display:flex;
        width: 50%;
        justify-content: space-around;
        align-items: center;
        list-style-type:none;
    }
</style>