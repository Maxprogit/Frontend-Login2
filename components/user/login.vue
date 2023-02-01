<template>
    <v-card class="cardLogin">
        <v-card-title>Login</v-card-title>
        
        <v-card-text>
            <v-form v-model="formularioValido">
                <v-text-field label="Correo Electronico"
                placeholder=" Correo Electronico" 
                v-model="CorreoElectronico"
                />
            </v-form>
        </v-card-text>
        <v-card-actions>
            Botones para iniciar sesion
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
        data() {
            return {
            formularioValido: false,
            CorreoElectronico: ''
            }
        }
    }
</script>

<style scoped> 
    .cardLogin {
        background-color: rgb(30, 100, 30);
        border-radius: 10px;
        width: 500px;
        height: 300px;
    }
</style>