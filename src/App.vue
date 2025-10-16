<template>
  <div class="container-fluid mt-3">
    <div class="row mb-3">
      <div class="col-md-6">
        <label for="filtroNombre" class="form-label">Filtrar por Nombre/Apellido:</label>
        <input
          id="filtroNombre"
          type="text"
          class="form-control"
          v-model="filtroNombre"
          placeholder="Ingrese nombre o apellido..."
          @input="actualizarFiltros"
        />
      </div>
      <div class="col-md-6">
        <label for="filtroDni" class="form-label">Filtrar por DNI:</label>
        <input
          id="filtroDni"
          type="text"
          class="form-control"
          v-model="filtroDni"
          placeholder="Ingrese DNI..."
          @input="actualizarFiltros"
        />
      </div>
    </div>
    <br />
    <div class="card-deck m-0">
      <div class="row">
        <div class="col" v-for="(persona, idx) in personasFiltradas" :key="idx">
          <div class="card mb-3">
            <div class="card-body">
              <h5 class="card-title">{{ getNombreCompleto(persona) }}</h5>
              <p class="card-text">dni {{ persona.dni }}</p>
              <a href="#" class="card-link">{{ persona.correo }}</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filtroNombre: '',
      filtroDni: '',
      personas: [
        { nombre: 'Daniel', apellido: 'Sanchez', correo: 'danielsanchez68@hotmail.com', dni: '20442873' },
        { nombre: 'Juan', apellido: 'Perez', correo: 'j@p.gmail.com', dni: '12345678' },
        { nombre: 'Ana', apellido: 'Suarez', correo: 'a@s.gmail.com', dni: '87654321' },
        { nombre: '...', apellido: '...', correo: '...', dni: '...' },
      ],
    }
  },
  computed: {
    personasFiltradas() {
      return this.personas.filter((p) => {
        // Filtro por nombre/apellido
        const nombreCompleto = `${p.nombre} ${p.apellido}`.toLowerCase()
        const cumpleFiltroNombre = this.filtroNombre === '' || 
          nombreCompleto.includes(this.filtroNombre.toLowerCase())
        
        // Filtro por DNI
        const cumpleFiltroDni = this.filtroDni === '' || 
          p.dni.includes(this.filtroDni)
        
        // Ambos filtros deben cumplirse (AND lógico)
        return cumpleFiltroNombre && cumpleFiltroDni
      })
    },
  },
  methods: {
    getNombreCompleto(p) {
      return `${p.nombre} ${p.apellido}`
    },
    actualizarFiltros() {
      // Este método se ejecuta cuando cambian los filtros
      console.log('Filtros actualizados:', {
        nombre: this.filtroNombre,
        dni: this.filtroDni
      })
    },
  },
}
</script>