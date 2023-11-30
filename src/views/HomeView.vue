<template>
<div class="row">
  <div class="col-lg-8 offset-lg-2 mt-4">
    <div class="table-responsive">
      <table class="table table-bordered table-striped">
        <thead>
          <tr>
            <th>#</th>
            <th>ID</th>
            <th>FOTO</th>
            <th>NOMBRE</th>
            <th>APELLIDO</th>
            <th>REGISTRO</th>
            <th>EDICION</th>

          </tr>
        </thead>
        <tbody class="table-group-divider" id="contenido">
          <tr v-if="this.cargando">
            <td colspan="6"><h3>Cargando...</h3></td>
          </tr>
          <tr v-else v-for="est, i in this.estudiantes" :key="est.id">
            <td v-text="(i+1)"></td>
            <td v-text="est.id"></td>
            <td v-text="est.foto"></td>
            <td v-text="est.nombre"></td>
            <td v-text="est.apellido"></td>
            <td v-text="est.create_add"></td>
            <td ></td>
          </tr>
        </tbody>
    </table>
    </div>
  </div>
</div>
</template>

<script>
  import axios from 'axios';
export default{
   data(){
    return{
      estudiantes:null,
      cargando:false
    }
 },
 mounted(){
  this.getEstudiantes();
 },
 methods:{
    getEstudiantes(){
      this.cargando = true;
      axios.get('http://lara-vue3.test/api/v1/estudiantes').then(
          res =>{
            this.estudiantes = res.data;
            this.cargando = false;
          }
      );
    }
 }
}

</script>
