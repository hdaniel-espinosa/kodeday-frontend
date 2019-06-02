<template>
    <nav class="navbar">
        <span class="navbar-item">
            <img class="navbar-logo" src="https://www.neoesfera.com/wp-content/uploads/2018/05/logo-perro.png">
            <h1 class="navbar-brand">Petcare</h1>
        </span>

        <span class="navbar-item">
            <Button text="inicia sesión" class="loggin"/>
            <Button text="registrar" class="register"/>
        </span>
    </nav>
</template>

<script>
import Button from './Button';

export default {
    name: 'Navbar',
    components: {
        Button
    }
}
</script>

<style scoped>
</style>