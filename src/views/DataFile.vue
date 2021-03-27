<template>
    
    <div id = "template1">{{account.username}} </div>
    
</template> 
<script>
export default {
    name: "DataFile",
    data() {
        return {
            account:{
                username: "admin",
                password: "1234",
            }
        }
    },

}
</script>

<style>
#template1{
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 50px;
    color: blanchedalmond;
}

</style>