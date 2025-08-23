# Sistema de Estilos Compartidos

Este directorio contiene el sistema de diseño y estilos compartidos para mantener la consistencia visual en toda la aplicación.

## Estructura de archivos

- **`_variables.scss`**: Todas las variables de diseño (colores, espaciado, tipografía, etc.)
- **`_mixins.scss`**: Mixins reutilizables para componentes comunes
- **`_components.scss`**: Clases CSS utilitarias y componentes predefinidos
- **`index.scss`**: Archivo principal que importa todos los demás

## Cómo usar

### En componentes Angular

```scss
// En tu archivo component.scss
@import '../../../app/shared/styles/index';

// Ahora puedes usar todas las variables y mixins
.mi-componente {
  @include card-base;
  background-color: $color-surface;
  padding: $spacing-md;
}
```

### Variables disponibles

#### Colores
- `$color-primary`: Color principal (#02BEC1)
- `$color-surface`: Fondo de superficies (#202837)
- `$color-background`: Fondo principal (#192230)
- `$color-success`, `$color-warning`, `$color-danger`: Estados

#### Espaciado (Sistema 8px)
- `$spacing-xs`: 4px
- `$spacing-sm`: 8px
- `$spacing-md`: 16px
- `$spacing-lg`: 24px
- `$spacing-xl`: 32px

### Mixins principales

#### Cards
```scss
.mi-card {
  @include card-base;  // Card básica con todos los estilos
  @include card-kpi;   // Card específica para KPIs
}
```

#### Tablas
```scss
.mi-tabla {
  @include table-base;      // Estilos base de tabla
  @include table-container; // Contenedor con scroll
}
```

#### Botones
```scss
.mi-boton {
  @include button-primary;   // Botón primario
  @include button-secondary; // Botón secundario
}
```

### Clases utilitarias

#### Botones
```html
<button class="btn btn-primary">Acción principal</button>
<button class="btn btn-secondary">Acción secundaria</button>
<button class="btn btn-danger">Eliminar</button>
```

#### Espaciado
```html
<!-- Márgenes: m-{0-5}, mt-, mr-, mb-, ml-, mx-, my- -->
<div class="mt-3 mb-2">Contenido con margen</div>

<!-- Padding: p-{0-5}, pt-, pr-, pb-, pl-, px-, py- -->
<div class="p-3">Contenido con padding</div>
```

#### Layout
```html
<div class="d-flex justify-content-between align-items-center">
  <span>Izquierda</span>
  <span>Derecha</span>
</div>
```

#### Badges
```html
<span class="badge badge-success">Activo</span>
<span class="badge badge-warning">Pendiente</span>
<span class="badge badge-danger">Error</span>
```

## Principios de diseño

1. **Consistencia**: Usar siempre las variables definidas
2. **Modularidad**: Preferir mixins sobre código duplicado
3. **Escalabilidad**: Sistema de 8px para espaciado
4. **Accesibilidad**: Contraste adecuado en colores
5. **Responsive**: Usar los mixins responsive definidos

## Mejores prácticas

1. **No hardcodear valores**: Siempre usar variables
   ```scss
   // ❌ Mal
   padding: 16px;
   color: #02BEC1;
   
   // ✅ Bien
   padding: $spacing-md;
   color: $color-primary;
   ```

2. **Usar mixins para componentes comunes**
   ```scss
   // ❌ Mal - Código duplicado
   .mi-card {
     background: #202837;
     border-radius: 8px;
     padding: 16px;
     box-shadow: 0 3px 6px rgba(0,0,0,0.16);
   }
   
   // ✅ Bien - Usar mixin
   .mi-card {
     @include card-base;
   }
   ```

3. **Responsive design**
   ```scss
   .mi-componente {
     padding: $spacing-sm;
     
     @include responsive('md') {
       padding: $spacing-md;
     }
     
     @include responsive('lg') {
       padding: $spacing-lg;
     }
   }
   ```