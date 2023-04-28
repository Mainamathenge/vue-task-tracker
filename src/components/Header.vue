<template>
    <header>
        <h1>{{ title }}</h1>
        <Button text = "Add Task " color = "green" />
    </header>
</template>
/* eslint-disable */
<script>
import Button from './Button'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name : 'Header_head',
    props : {
        title :{
            type : String,
            default : 'hello World',
        }
    } ,
    components : {
        Button
    }
}

</script>

<style scoped>
    header {
       display: flex; 
       justify-content: space-between;
       align-items: center;
       margin-bottom: 20 ;
       
    }
</style>