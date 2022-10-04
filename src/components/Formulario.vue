<template>
  <!-- <form @submit.prevent="sumbit()">
        <div class="mb-3">
            <label for="name" class="form-label">Name:</label>
            <input v-model="nombre" type="text" name="" id="name" placeholder="nombre:" required class="form-control" aria-describedby="emailHelp">
            <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
            <label for="edad" class="form-label">Edad:</label>
            <input v-model="edad" type="number" name="" id="edad" min="18" max="60" placeholder="edad:" required class="form-control" aria-describedby="emailHelp">
            <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            <input v-model="email" type="email" name="" id="email" placeholder="correo@mail.com" required class="form-control" aria-describedby="emailHelp">
            <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <button type="submit" class="btn btn-primary">Enviar</button>
    </form> -->
  <div class="row">
    <div class="col-12">
      <barra-progreso :porcentajeCompletado="porcentajeCompletado"/>
    </div>
    <div class="col-12 col-md-4">
      <div>
        <form @submit.prevent="registrar()">
          <div class="mb-3">
            <label for="proyecto" class="form-label">Proyecto</label>
            <input v-model.trim="proyecto" type="text" id="proyecto" class="form-control" required>
          </div>
          <div class="mb-3">
            <label for="actividad" class="form-label">Actividad</label>
            <select v-model="actividad" name="" id="actividad" class="form-select" required>
              <option selected value="1">Aplicacion web con Vue.js</option>
              <option value="2">Aplicacion backend con node.js</option>
              <option value="3">App movil con React Native</option>
            </select>
          </div>
          <div class="mb-3">
            <label for="guardar" class="form-check-label">Guardar</label>
            <input v-model="guardar" type="checkbox" id="guardar" class="form-check-input">
          </div>
          <button type="submit" class="btn btn-outline-info">Enviar</button>
        </form>
      </div>
    </div>
    <div class="col-12 col-md-8">
      <tareas 
      :numeroElementos="numeroElementos" 
      :proyectos="proyectos"
      :cambiarEstado="cambiarEstado"
      :limpiarProyectos="limpiarProyectos"/>      
    </div>
  </div>


  <!-- <div class="container">
      <p>Proyecto:{{proyecto}}</p>
      <p>Actividad:{{actividad}}</p>
      <p>Guardar:{{guardar}}</p>
    </div> -->
</template>


<script>
import BarraProgreso from './BarraProgreso.vue';
import Tareas from './Tareas.vue';
export default {
  components: { BarraProgreso,Tareas},
  data: () => ({
    nombre: "",
    edad: 18,
    email: "",
    proyecto: "",
    actividad: "",
    guardar: false,
    proyectos: []
  }),
  methods: {
    registrar() {
      // console.log("submit");
      // console.log(`${this.nombre} ${this.edad} ${this.email}`);
      const proyecto = {
        "proyecto": this.proyecto,
        "actividad": this.actividad,
        "guardar": this.guardar,
        "finalizado": false
      }
      this.proyectos.push(proyecto);
      localStorage.setItem("proyectos",JSON.stringify(this.proyectos));
      console.log(this.proyectos);
    },
    cambiarEstado(proyecto,parametro) {
      //this.proyectos[index][parametro] = !this.proyectos[index][parametro];
      proyecto[parametro]=!proyecto[parametro];
      localStorage.setItem("proyectos",JSON.stringify(this.proyectos));
    },
    limpiarProyectos(){
      this.proyectos=[];
      localStorage.removeItem("proyectos");
      //localStorage.clear();
    }
  },
  computed: {
    numeroElementos() {
      return this.proyectos.length;
    },
    porcentajeCompletado(){
      let c=0;
      this.proyectos.map((p)=>{
        if(p.finalizado){
          c++;
        }
      });
      return c/this.proyectos.length*100||0;
    }
  },
  mounted(){
    this.proyectos=JSON.parse(localStorage.getItem("proyectos"))||[];
  }
}
</script>