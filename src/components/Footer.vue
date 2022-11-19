<template>
    <footer>
        <img :src="logo" :alt="alt" id="logo">
        <p> OASIS BURGUERS &COPY; 2022</p>
    </footer>
</template>
<script>
export default {
    name:"Footer",
    props:["logo", "alt"]
}
</script>

<style scoped>
footer{
    height: 200px;
    background-color: #e70f0f;
    border-top: 4px solid #e70f0f;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

p{
    padding: 0 30px;
    font-weight: bolder;
}

#logo{
    width: 130px;
    height: 120px;
    align-items: center;
}

</style>