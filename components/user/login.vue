<template>
    <v-card class="cardLogin">
        <v-card-title class="title">Inicia Sesion</v-card-title>
        
        <v-card-text>
            <v-row>
                <v-col cols="4" align-self="center">
                    <img src="../../assets/images/kenny.png" class="imgLogin">
                </v-col>
                <v-col cols="8" align-self="center">
                    <v-form ref="formLogin">
                        <v-text-field label="Correo Electronico"
                        placeholder=" Correo Electronico" 
                        v-model="CorreoElectronico"
                        :rules="validarCorreo"
                        />
                        <v-text-field label="Password"
                        placeholder="Password" 
                        v-model="Password"
                        :rules="validarPassword"
                        />
                    </v-form>
                </v-col>
            </v-row>
           
        </v-card-text>
        <v-card-actions>
            <v-btn class="btnLogin"
                rounded
                block
                @click="loginBackend"
            >
                Iniciar Sesion
            </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
        data() {
            return {
            CorreoElectronico: '',
            validarCorreo: [
                v => !v || /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
                ],
            Password: '',
            validarPassword: [
                value => value.length >= 6 || 'Min 6 characters',
                ]
            }
        },
        methods: {
            loginBackend () {
                const valid = this.$refs.formLogin.validate()
                if(valid){
                    alert('Presionaste el boton')
                } else {
                    alert('No cumpliste con las reglas')
                }
                
            }
        }
    }
</script>

<style scoped> 
    .cardLogin {
        background-color: rgb(99, 168, 99);
        border-radius: 10px;
        width: 500px;
        height: 300px;
    }
    .imgLogin {
        width: 85%;
        height: 85%;
    }
    .btnLogin {
        background-color: grey!important;
        color: rgb(126, 97, 53);
    }
    .title {
        font-size: 25px;
        color: rgb(126, 97, 53);
        justify-content: center;
        font-weight: 200;
    }
</style>