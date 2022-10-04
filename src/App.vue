<template>
  <div>
    <Header/>
    <Formulario/>
  </div>
</template>
<script>
  import Header from "./components/Header.vue";
  import Formulario from "./components/Formulario.vue";
  export default{
    data:()=>({
      nombre:"",
      edad:18,
      email:""
    }),
    methods:{
      sumbit(){
        console.log("submit");
        console.log(`${this.nombre} ${this.edad} ${this.email}`);
      }
    },
    components:{
      Header,
      Formulario
    }
  }
</script>
<style scoped>

</style>