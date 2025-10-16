# NT2 - Trabajo Práctico No 2

## Directorio de Personas - Sistema de Búsqueda y Filtrado

Este proyecto implementa un sistema de directorio de personas con funcionalidades avanzadas de búsqueda y filtrado desarrollado en Vue 3 con Vite.

## Consignas del Trabajo Práctico

### ✅ 1. Fork del repositorio
**Consigna:** Hacer un fork del repositorio https://github.com/danielsanchez68/nt2-21d-ejercicio2 para tener el código en la cuenta de Github de cada uno de ustedes, separándolo del versionado del repositorio original.

**Estado:** ✅ Completado
- Repositorio forkeado y configurado correctamente

### ✅ 2. Conversión a Vue CLI
**Consigna:** Clonar este repositorio en la máquina local, luego convertir el proyecto Vue CDN a Vue CLI con Vite.

**Estado:** ✅ Completado
- **Commit:** [8448c8d](https://github.com/atomiclab/nt2-21d-ejercicio2/commit/8448c8d) - "conversion a CLI"
- Proyecto convertido exitosamente de Vue CDN a Vue CLI con Vite
- Configuración completa de dependencias y estructura del proyecto

### ✅ 3. Implementación de filtros de búsqueda
**Consigna:** Modificar la funcionalidad original, agregando dos filtros de búsqueda: uno por nombre (o nombre + apellido) y otro por dni. Pensar que necesitan agregar en el proyecto Vue CLI para obtener los valores de esos filtros mientras van cambiando.

**Estado:** ✅ Completado
- **Commit:** [df2a40f](https://github.com/atomiclab/nt2-21d-ejercicio2/commit/df2a40f) - "Modificar la funcionalidad original, agregando dos filtros de búsqueda: uno por nombre (o nombre + apellido) y otro por dni. Pensar que necesitan agregar en el proyecto Vue CLI para obtener los valores de esos filtros mientras van cambiando."
- Implementados dos filtros separados:
  - Filtro por nombre/apellido
  - Filtro por DNI
- Utilización de `v-model` para binding bidireccional
- Implementación de computed properties reactivas
- Eventos `@input` para detectar cambios en tiempo real

### ✅ 4. Lógica de filtros excluyente
**Consigna:** Si el filtro está vacío quedará deshabilitado. El usuario puede llenar un sólo filtro o los dos y el resultado tiene que ser excluyente.

**Estado:** ✅ Completado
- **Commit:** [3aa7e29](https://github.com/atomiclab/nt2-21d-ejercicio2/commit/3aa7e29) - "Si el filtro está vacío quedará deshabilitado. El usuario puede llenar un sólo filtro o los dos y el resultado tiene que ser excluyente. Agregue que se ponga en gris cuando estan deshabilitados para visualizarlo"
- Lógica OR implementada: los resultados deben cumplir al menos uno de los filtros habilitados
- Filtros vacíos se consideran deshabilitados
- Indicadores visuales con estilos CSS para filtros deshabilitados (gris)

### ✅ 5. Alert de advertencia
**Consigna:** Disponer de un cartel maquetado con Bootstrap (puede ser un alert) debajo de los filtros que sólo muestre como advertencia cuando el usuario no haya ingresado al menos 3 caracteres en alguno de los filtros.

**Estado:** ✅ Completado
- **Commit:** [131d448](https://github.com/atomiclab/nt2-21d-ejercicio2/commit/131d448) - "Disponer de un cartel maquetado con Bootstrap (puede ser un alert) debajo de los filtros que sólo muestre como advertencia cuando el usuario no haya ingresado al menos 3 caracteres en alguno de los filtros."
- Alert de Bootstrap implementado con clase `alert-warning`
- Computed property `mostrarAdvertencia` que evalúa la longitud de los filtros
- Alert dismissible con botón de cierre
- Icono de advertencia con Bootstrap Icons

### ✅ 6. Mejoras de estilo y header
**Consigna:** Subir la solución al repositorio remoto propio.

**Estado:** ✅ Completado
- **Commit:** [1f43b83](https://github.com/atomiclab/nt2-21d-ejercicio2/commit/1f43b83) - "estilo"
- Header "Directorio de Personas" agregado
- Mejoras visuales implementadas
- Código subido al repositorio remoto

## Tecnologías Utilizadas

- **Vue 3** - Framework de JavaScript reactivo
- **Vite** - Herramienta de construcción rápida
- **Bootstrap 5** - Framework CSS para diseño responsive
- **JavaScript ES6+** - Funcionalidades modernas

## Funcionalidades Implementadas

### 🔍 Sistema de Filtrado
- **Filtro por Nombre/Apellido:** Búsqueda case-insensitive en nombre completo
- **Filtro por DNI:** Búsqueda exacta en el campo DNI
- **Lógica Excluyente:** Los resultados cumplen al menos uno de los filtros habilitados
- **Filtros Deshabilitados:** Campos vacíos no afectan los resultados

### 🎨 Interfaz de Usuario
- **Header Profesional:** Título "Directorio de Personas"
- **Indicadores Visuales:** Filtros deshabilitados aparecen en gris
- **Alert de Advertencia:** Notificación cuando se ingresan menos de 3 caracteres
- **Diseño Responsive:** Adaptable a diferentes tamaños de pantalla

### ⚡ Reactividad
- **Tiempo Real:** Los filtros se aplican mientras el usuario escribe
- **Computed Properties:** Cálculos automáticos de resultados filtrados
- **Event Binding:** `v-model` y `@input` para interacción inmediata

## Estructura del Proyecto

```
src/
├── App.vue              # Componente principal con toda la lógica
├── main.js              # Punto de entrada de la aplicación
├── style.css            # Estilos globales
└── components/
    └── HelloWorld.vue   # Componente de ejemplo (no utilizado)
```

## Instalación y Ejecución

```bash
# Instalar dependencias
npm install

# Ejecutar en modo desarrollo
npm run dev

# Construir para producción
npm run build

# Vista previa de la construcción
npm run preview
```

## Autor

**Gino Tubaro** - [@atomiclab](https://github.com/atomiclab)

## Repositorio Original

Fork de: https://github.com/danielsanchez68/nt2-21d-ejercicio2
