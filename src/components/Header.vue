<template>
    <div class="row container">
        <div class="col-12 col-md-3">
            <h1>Formularios</h1>
        </div>
        <div class="col-12 col-md-8">
            <img src="https://cdn.svgporn.com/logos/linux-tux.svg?response-content-disposition=attachment%3Bfilename%3Dlinux-tux.svg" alt="">   
        </div>
    </div>
</template>
<script>
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
    }
  }
</script>