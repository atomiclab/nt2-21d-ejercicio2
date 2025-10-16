<template>
  <div class="container-fluid mt-3">
    <div class="row mb-3">
      <div class="col-md-6">
        <label for="filtroNombre" class="form-label">Filtrar por Nombre/Apellido:</label>
        <input
          id="filtroNombre"
          type="text"
          class="form-control"
          :class="{ 'filtro-deshabilitado': filtroNombre.trim() === '' }"
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
          :class="{ 'filtro-deshabilitado': filtroDni.trim() === '' }"
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
        // Verificar si los filtros están habilitados (no vacíos)
        const filtroNombreHabilitado = this.filtroNombre.trim() !== ''
        const filtroDniHabilitado = this.filtroDni.trim() !== ''
        
        // Si ningún filtro está habilitado, mostrar todas las personas
        if (!filtroNombreHabilitado && !filtroDniHabilitado) {
          return true
        }
        
        // Verificar cumplimiento de cada filtro habilitado
        let cumpleFiltros = false
        
        // Filtro por nombre/apellido (si está habilitado)
        if (filtroNombreHabilitado) {
          const nombreCompleto = `${p.nombre} ${p.apellido}`.toLowerCase()
          const cumpleFiltroNombre = nombreCompleto.includes(this.filtroNombre.toLowerCase())
          cumpleFiltros = cumpleFiltros || cumpleFiltroNombre
        }
        
        // Filtro por DNI (si está habilitado)
        if (filtroDniHabilitado) {
          const cumpleFiltroDni = p.dni.includes(this.filtroDni)
          cumpleFiltros = cumpleFiltros || cumpleFiltroDni
        }
        
        // Resultado excluyente: debe cumplir al menos uno de los filtros habilitados
        return cumpleFiltros
      })
    },
  },
  methods: {
    getNombreCompleto(p) {
      return `${p.nombre} ${p.apellido}`
    },
    actualizarFiltros() {
      // Este método se ejecuta cuando cambian los filtros
      // La reactividad de Vue se encarga de actualizar automáticamente
      // la computed property personasFiltradas
      const filtroNombreHabilitado = this.filtroNombre.trim() !== ''
      const filtroDniHabilitado = this.filtroDni.trim() !== ''
      
      console.log('Filtros actualizados:', {
        nombre: this.filtroNombre,
        dni: this.filtroDni,
        nombreHabilitado: filtroNombreHabilitado,
        dniHabilitado: filtroDniHabilitado
      })
    },
  },
}
</script>

<style scoped>
.filtro-deshabilitado {
  background-color: #f8f9fa !important;
  color: #6c757d !important;
  border-color: #dee2e6 !important;
  opacity: 0.7;
}

.filtro-deshabilitado::placeholder {
  color: #adb5bd !important;
  opacity: 1;
}

.filtro-deshabilitado:focus {
  background-color: #f8f9fa !important;
  border-color: #dee2e6 !important;
  box-shadow: 0 0 0 0.2rem rgba(108, 117, 125, 0.25) !important;
}
</style>