<template>
<div>
    <button type="button" v-on:click=ViewNotes()>{{ button_text }}</button>
</div>
</template>
<script>
    export default{
        data(){
            return{
                button_text:"VIEW MY NOTES"
            }
        }
    }
</script>