<template>
  <div class="container-fluid mt-3">
    <input
      type="text"
      class="form-control"
      v-model="criterioDeBusqueda"
      placeholder="Ingresar un criterio de busqueda..."
    />
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
      criterioDeBusqueda: '',
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
        const t = `${p.nombre} ${p.apellido} ${p.dni} ${p.correo}`
        return t.toLowerCase().includes(this.criterioDeBusqueda.toLowerCase())
      })
    },
  },
  methods: {
    getNombreCompleto(p) {
      return `${p.nombre} ${p.apellido}`
    },
  },
}
</script>