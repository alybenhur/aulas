<script setup>
 import {reactive} from 'vue'
 const asignatura = reactive({
     id_asignatura : '',
     nombre : ''
   })

   const asignaturas = reactive([])

   const estudiantes = reactive([])

   const estudiante= reactive({
     cedula : '',
     nombre : '',
     apellido : '',
     edad : '',
     correo : '',
   })

    function guardar(){
      asignaturas.push({...asignatura})
      limpiar()
    }

     function guardaralumno(){
      estudiantes.push({...estudiante})
      limpiarestudiante()
    }

    function limpiarestudiante(){
      estudiante.cedula = ''
      estudiante.nombre = ''
      estudiante.apellido = ''
      estudiante.edad = ''
      estudiante.correo = ''
    }

    function limpiar(){
      asignatura.id_asignatura = ''
      asignatura.nombre = ''
    }

</script>

<template>
<div>
   
   
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class=" container container-fluid">
    <a class="navbar-brand" href="#">SISTEMA INTELIGENTE DE NOTAS</a>
   
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        
        
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Asignatura
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#exampleModal">Crear</a></li>
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#exampleModal2">Listar</a></li>
           
          </ul>
        </li>
          <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
           Estudiante
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#vetanaalumno">Crear</a></li>
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#exampleModal2">Listar</a></li>
           
          </ul>
        </li>
        
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>

<!-- VENTANA ASIGNATURA -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">REGISTRAR ASIGNATURA</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
         <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingInput" placeholder="codigo asignatura" v-model="asignatura.id_asignatura">
            <label for="floatingInput">Codigo asignatura</label>
        </div>
        <div class="form-floating">
            <input type="text" class="form-control" id="floatingPassword" placeholder="Nombre asignatura" v-model="asignatura.nombre">
            <label for="floatingPassword">Nombre Asignatura</label>
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button type="button" class="btn btn-primary" @click="guardar">Guardar</button>
      </div>
    </div>
  </div>
</div>


  <!-- VENTANA LISTAR ASIGNATURA -->
<div class="modal fade" id="exampleModal2" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">REGISTRAR ASIGNATURA</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <table class="table table-striped table-hover">
            <thead>
              <tr>
                <th scope="col">Id</th>
                <th scope="col">Nombre</th>
               </tr>
            </thead>
            <tr v-for="data in asignaturas ">
              <td>{{ data.id_asignatura }}</td>
              <td>{{ data.nombre }}</td>
            </tr>
        </table>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button type="button" class="btn btn-primary" @click="guardar">Guardar</button>
      </div>
    </div>
  </div>
</div>

<!-- VENTANA Alumno -->
<div class="modal fade" id="vetanaalumno" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">REGISTRAR ALUMNO</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
         <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingInput" placeholder="Cedula Estudiante" v-model="estudiante.cedula"> 
            <label for="floatingInput">Cedula Estudiante</label>
        </div>
        <div class="form-floating  mb-3">
            <input type="text" class="form-control" id="floatingPassword" placeholder="Nombre estudiante" v-model="estudiante.nombre">
            <label for="floatingPassword">Nombre Estudiante</label>
        </div>
         <div class="form-floating mb-3">
            <input type="text" class="form-control" id="floatingInput" placeholder="Apellido Estudiante" v-model="estudiante.apellido">
            <label for="floatingInput">Apellido Estudiante</label>
        </div>
        <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingPassword" placeholder="Edad Estudiante" v-model="estudiante.edad">
            <label for="floatingPassword">Edad Estudiante</label>
        </div>
         <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="Correo estudiante" v-model="estudiante.correo">
            <label for="floatingInput">Correo Estudiante</label>
        </div>
      


      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button type="button" class="btn btn-primary" @click="guardaralumno">Guardar</button>
      </div>
    </div>
  </div>
</div>

</div>

</template>

<style scoped>


</style>
