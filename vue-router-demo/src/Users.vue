<template>
    <div>
        <h1>This is Users!</h1>
        <p>team id is : {{ $route.params.teamID }}</p>
        <button @click="goHome">go home</button>
    </div>
</template>

<script>

    export default{

        watch: {
            '$route' (to , from){
                alert(to.params.teamID);
            }
        },

        created(){
            alert(this.$route.params.teamID)
        },

        methods:{
            goHome(){
                this.$router.push('/');
            }
        }
    }
</script>