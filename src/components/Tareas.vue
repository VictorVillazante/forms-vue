<template>
  <h2>Numero de elementos {{numeroElementos}}</h2>
    <div class="row">
      <div class="col-6">
        Limpiar proyectos
      </div>
      <div class="col-6">
        <button class="btn btn-warning" @click="limpiarProyectos()">Clear</button>
      </div>
    </div>
      <div class="table-responsive">
        <table class="table table-dark table-hover">
          <thead>
            <tr>
              <th>#</th>
              <th>Proyecto</th>
              <th>Actividad</th>
              <th>Guardar</th>
              <th>Completado</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(proyecto,index) in proyectos" :key="index">
              <td>
                {{index+1}}
              </td>
              <td>
                {{proyecto.proyecto}}
              </td>
              <td>
                {{proyecto.actividad}}
              </td>
              <td @click="cambiarEstado(proyecto,'guardar')" :class="proyecto.guardar?'bg-success':'bg-danger'">
                {{proyecto.guardar?'SI':'NO'}}
              </td>
              <td @click="cambiarEstado(proyecto,'finalizado')" :class="proyecto.finalizado?'bg-success':'bg-danger'">
                {{proyecto.finalizado?'SI':'NO'}}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
</template>

<script>
export default {
    props:["numeroElementos","proyectos","cambiarEstado","limpiarProyectos"]
}
</script>

<style>

</style>