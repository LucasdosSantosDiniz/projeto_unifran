<template>
    <div class="message-container">
        <p>{{msg}}</p>
    </div>
</template>
<script>
export default {
    name: "Message",
    props:{
        msg:String
    }
}
</script>
<style scoped>
.message-container{
    color:red;
    background-color: yellow;
    border: 2px solid red;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}
</style>