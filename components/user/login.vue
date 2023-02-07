<template>
  <v-card class="cardLogin">
    <v-card-title class="title">Iniciar Sesión</v-card-title>
      <v-card-text>
            <v-row justify="center" align="center">
              <v-col cols="4" align-self="center">
                <img src="../../assets/images/kenny.png" alt="" class="imgLogin">
              </v-col>
              <v-col cols="8" align-self="center">
                <v-form ref="formLogin">
                  <v-text-field label="Correo Electrónico" placeholder="Correo electronico" v-model="correoElectronico" :rules="validarCorreo"/>
                  <v-text-field label="Password" placeholder="Password" v-model="password" :rules="validarPassword"/>
                </v-form>
              </v-col>
            </v-row>
      </v-card-text>
        
      <v-card-actions>
        <v-btn class="btnLogin" rounded block @click='loginBackend'>
          Login
        </v-btn>
      </v-card-actions>
  </v-card>
</template>

<script>
import { async } from 'q'

    export default{
        data(){
            return{
                correoElectronico: '',
                validarCorreo:[
                    v => !v || /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
                ],
                password: '',
                validarPassword:[
                    value => value.length >= 6 || 'Minimo 6 caracteres'
                    ]
                }
                
        },

        methods:{
            async loginBackend (){
                const valid = this.$refs.formLogin.validate()
                if(valid){
                    const sendData = {
                        email: this.correoElectronico,
                        password: this.password
                    }
                    await this.$auth.loginWith('local',{
                        data: sendData
                    }).then(async (res) =>{
                        console.log('Respuesta del back:', res)
                        if(res.data.error == null){
                            this.$router.push('/dashboard')
                        }
                    }).catch((error) =>{
                        console.log('error: ', error)
                    })
                }else{
                    alert('No cumples las reglas')
                }
                
            }
        }
    }
</script>

<style scoped>
    .cardLogin{
        background-color:#00ffc8;
        border-radius: 10px;
        width: 500px;
        height: 300px;
    }

    .imgLogin{
        width: 100%;
        border-radius: 10px;

    }

    .btnLogin{
        background-color: rgb(104, 179, 211) !important;
        color: black;
        
    }

    .title{
        font-size: 30px;
        justify-content: center;
        color: rgb(0, 0, 0);
        font-weight: 700;
    }
</style>