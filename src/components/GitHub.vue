<template>
    <div class="container-fluid">
        <div class="row align-items-center">
            <h1 class="text-center">Buscar usuario de GitHub</h1>
        </div>
        <div class="row align-items-center">
            <label for="nombre">Nombre Usuario GitHub: </label>
            <input type="text" name="nombre" id="nombre" v-model="usuario" v-on:keydown.enter="obtenerUsuario">
            <h4 class="text-danger" v-if="usuarionoexiste">¡El usuario no existe!</h4> 
        </div>
        <div class="row">
            <div class="col-6 align-items-center mt-3"  v-if="usuarioValido">
                <p>Usuario:</p>
                <hr>
                <p>Avatar: <img class="img-thumbnail" width="300" :src="datosUsuario.avatar_url" alt="avatar"></p>
                <p>Usuario: {{ datosUsuario.login }}</p>
                <a class="link" :href="datosUsuario.html_url">URL Usuario</a>
                <button class="btn btn-secondary" type="button" @click="obtenerRepos" name="Repositorios">Repositorios</button>
            </div>
            <div class="col-6 mt-3" v-if="repoVisible">
                <p>Repositorio  /  Forks</p>
                <hr>
                <GitHubRepo v-for="r in repositorios" :key="r.id" :repo="r"></GitHubRepo>
            </div>
        </div>
    </div>
</template>

<script>
    import GitHubRepo from './GitHubRepo.vue';

    export default {
        name: "GitHub",
        components: {
            GitHubRepo
        },
        data(){
            return{
                usuario: "",
                info: "",
                repositorios: [],
                usuarionoexiste: false,
                usuarioValido: false,
                datosUsuario: null,
                repoVisible: false
                // desactivar campo búsqueda al pulsar intro, activar al recibir datos
            }
        },
        methods: {
            obtenerUsuario: function(){
                this.usuarionoexiste = false;
                this.repoVisible = false;

                let url = `https://api.github.com/users/${this.usuario}`;
                
                fetch(url)
                .then(response => {
                    if(response.ok){
                        return response.json();
                    }
                    else{
                        throw new Error ("El usuario no existe.");
                    }
                })
                .then(resultado => {
                    this.datosUsuario = resultado;
                    this.usuarioValido = true;
                })
                .catch(error => {
                    console.log(error);
                    this.usuarionoexiste = true;
                    this.usuarioValido = false;
                })
            },
            obtenerRepos: function(){
                
                // let url = `https://api.github.com/users/${this.usuario}/repos`;
                let url = this.datosUsuario.repos_url;
                
                fetch(url)
                .then(response => {
                    if(response.ok){
                        return response.json();
                    }
                    else{
                        throw new Error ("No se encuentran repositorios.");
                    }
                })
                .then(resultado => {
                    this.repositorios = resultado;
                    this.usuarioValido = true;
                    this.repoVisible = true;
                })
                .catch(error => {
                    console.log(error);
                    this.usuarioValido = false;
                    this.repoVisible = false;
                    
                })
            }
        }
    }
</script>

<style scoped>

</style>