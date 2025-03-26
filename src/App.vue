<template>
  <div>
    <GitHub></GitHub>
  </div>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<script>
  import GitHub from './components/GitHub.vue'

  export default{
    name: 'app',
    components: {
      GitHub
    },
    data(){
      return{
        
      }
    },
    methods:{

    },
    computed: {
      
    }
  }
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
</script>

<style scoped>
*{
    margin:0;
    padding: 0%;
    width: 100%;
}
</style>
