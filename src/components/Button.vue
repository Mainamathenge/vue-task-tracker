<template>
    <button @click = "onclick()" :style="{background : color}" class="btn"> {{ text }} </button>
</template>

<script>
    export default{
       // eslint-disable-next-line vue/multi-word-component-names
       name :  'Button',
       props : {
        text :String,
        color : String
       },
       methods : {
            onclick(){
                console.log('click')
            },
       },

    }
</script>