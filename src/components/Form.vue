<template>

<form @submit.prevent="login">
    <label for="nome">
        <p>Nome:</p>
        <input type="text" v-model="user.nome" placeholder="nome" name="nome">
    </label>
    <label for="password">
        <p>Senha: </p>
        <input type="password" name="senha" v-model="user.senha" autocomplete="new-password">
    </label>

    <section>
        <button type="submit">enviar</button>
    </section>
</form>

</template>

<script setup>

    import { reactive } from "vue";
    import api from "./Axios"

    const user = reactive({
        nome: "",
        senha: ""
    })

    function login(){
        api.post("/round-code", user)
            .then(res => console.log(res))
            .catch(err => console.log(err))
    }

</script>

<style>
    form{
        color: #fff;
    }
</style>