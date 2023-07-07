<!---------------- Script ----------------->

<script>


</script>








<!--------------- Template ------------->

<template>
  
    <header>
        <div class="container">

            <div class="logo">
                <img src="../assets/img/Beholder.png" alt="Logo">
                <h1>BeholderFlix</h1>
            </div>

            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Film</a></li>
                    <li><a href="#">Serie Tv</a></li>
                    <li><a href="#">Acquista</a></li>

                </ul>
            </nav>

        </div>
    </header>
   

</template>







<!---------------Style -------------->

<style lang="scss" scoped>

    @use '../assets/scss/vars' as *;


    header {
        height: 100px;
        background-color: $secondaryCol;
        margin-bottom: 40px;
    }

    .container {
        height: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: white;
    }


    .logo {
        display: flex;
        align-items: center;
    }

    img {
        width: 100px;
        margin-right: 15px;
    }

    h1 {
        font-size: 60px;
        color: $primaryCol;
    }

    ul {
        display: flex;
        gap: 15px;

    }

    li {
        font-size: 25px;
        list-style-type: none;

        &::after {
            content: '';
            width: 0%;
            height: 4px;
            background-color: $primaryCol;
            display: blocK;
            margin: auto;
            transition: 0.5s;
        }

        &:hover::after {
            width: 100%;
        }
    }

    a {
        text-decoration: none;
        color: white;
    }

</style>
