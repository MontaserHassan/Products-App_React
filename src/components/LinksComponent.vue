<template>

    <div class="sidebar">
        <a class="active" href="#home">Home</a>
        <a href="#news">News</a>
        <a href="#contact">Contact</a>
        <a href="#about">About</a>
      </div>

</template>

<script>

    export default {
        data:()=>({
        }),
        methods: {
        
        },
        components: {
        },
        computed: {

        }
    };

</script>

<style>

    .sidebar {
        margin: 0;
        padding: 0;
        background-color: #f1f1f1;
    }
    
    .sidebar a {
        display: block;
        color: black;
        padding: 16px;
        text-decoration: none;
    }
    
    .sidebar a.active {
        background-color: #04AA6D;
        color: white;
    }
    
    .sidebar a:hover:not(.active) {
        background-color: #555;
        color: white;
    }
  
    @media screen and (max-width: 700px) {
        .sidebar {
        width: 100%;
        height: auto;
        }
        .sidebar a {float: left;}
    }
  
    @media screen and (max-width: 400px) {
        .sidebar a {
        text-align: center;
        float: none;
        }   
    }

</style>