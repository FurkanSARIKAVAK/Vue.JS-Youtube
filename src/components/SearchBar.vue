<template>
  <div>
    <form class="searchForm" @submit.prevent="handleSubmit">
        <input id="search" name="searchTerm" placeholder="Video ara..." autocomplete="on" class="searchInput" v-model="searchTerm" type="text">
        <button class="searchBtn" type="submit">Ara</button>
    </form>
  </div>
</template>

<script>
export default {
    emits:['termChange'],
    data(){
        return{
            searchTerm:'',
        }
    },
    methods: {
        handleSubmit(){
            this.$emit('termChange',this.searchTerm);
            this.searchTerm=''
        }
    },
}
</script>

<style scoped>
.searchForm {
    display: flex;
    margin: 20px 0px;
}
.searchInput {
    width: 85%;
    padding: 8px;
    margin-right: 20px;
    border-radius: 20px;
}
.searchBtn {
    width: 15%;
    border: none;
    background: rgb(206, 20, 20);
    color: white;
    font-size: 18px;
    font-family: 'Lucida Sans Regular', 'Lucida Grande', Geneva, Verdana, sans-serif;
    border-radius: 20px;
    cursor: pointer;
}

.searchBtn:hover {
    background: rgb(124, 6, 6);
}
</style>