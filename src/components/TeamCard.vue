<template>
    <div class="container">    
        <img class="card-img-top member" v-bind:src = member.image alt="Miembro del equipo">
        <div class="card-body">
            <p class="cabecera" style="text-align: center">Team Member<span> {{ member.codigo }}:  {{ member.rol }}</span></p>
            <h5 class="card-title">{{ member.nombre }}</h5>
            <p class="card-text">{{ member.descripcion }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "TeamCard",
        props: ['member']
    }
</script>

<style>
    .container{

        min-height: 560px;
        padding: 10px;
        background: rgba(11, 51, 1, 0.507);
        border-radius: 10px;
    }


    .card-body{

        padding-left: 0px;
        padding-right: 0px;
        padding-top: 5px;
        padding-bottom: 5px;
    }

    .card-body > p{

        text-align: justify;
        margin-bottom: 0px;
    }

    .code{

        font-size: 25px;
    }

    .member{

        height: 230px;
    }
</style>