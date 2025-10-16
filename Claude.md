src/
│
├── components/                      # Componentes UI reutilizables
│   ├── common/                     # Componentes genéricos como botones, tablas, inputs, modales, etc.
│   ├── layout/                     # Estructura visual general: Navbar, Sidebar, Footer, etc.
│   └── [Entidad]/                  # Componentes específicos por entidad (clientes, productos, etc.)
│       ├── Formulario[Entidad].jsx # Formulario dinámico para crear/editar la entidad
│       ├── Tabla[Entidad].jsx      # Tabla con listado de registros de la entidad
│       ├── Detalle[Entidad].jsx    # Vista detalle de un registro específico
│       └── Modal[Entidad].jsx      # Modal reutilizable para operaciones relacionadas con la entidad
│       └── …                       # Otros componentes específicos de la entidad
│
├── modules/                        # Módulos grandes si es una app extensa (ej: compras, ventas)
│   ├── [ModuloA]/                  # Lógica, vistas y subcomponentes del Módulo A
│   ├── [ModuloB]/                  # Lógica, vistas y subcomponentes del Módulo B
│   └── ...                         # Otros módulos escalables del sistema
│
├── features/                       # Funcionalidades transversales, no ligadas a una entidad
│   ├── auth/                       # Inicio de sesión, manejo de token, sesión de usuario
│   ├── notificaciones/             # Sistema de notificaciones in-app o toast
│   ├── permisos/                   # Control de accesos, roles y permisos
│   └── ...                         # Otras funcionalidades globales como multilenguaje, temas, etc.
│
├── hooks/                          # Hooks reutilizables y personalizados
│   ├── useMock/                    # Hooks para cargar datos simulados (modo desarrollo)
│   │   ├── useMock.js              # Hook genérico para cargar cualquier mock
│   │   ├── useMock[Entidad].js     # Hook específico para la entidad simulada
│   │   └── ...                     # Otros mocks reutilizables
│   ├── useApi/                     # Hooks para conexión real a APIs externas o backend
│   │   ├── use[Entidad]Api.js      # Hook específico para CRUD de la entidad en API real
│   │   └── ...                     # Otros hooks de API para diferentes entidades
│   ├── usePagination.js            # Lógica de paginación reutilizable
│   ├── useFilters.js               # Lógica de filtrado reutilizable
│   ├── useFormValidation.js        # Validación desacoplada para formularios
│   └── useDebounce.js              # Control de tiempo para inputs (ej: búsqueda)
│   └── …                           # Otros hooks reutilizables y especializados
│
├── mocks/                          # Datos simulados centralizados por entidad
│   ├── [entidad].js                # Datos fake de ejemplo para la entidad
│   └── auth.js                     # Datos simulados para login/autenticación
│   └── user.js                     # Datos simulados de usuarios
│   └── …                           # Otros datos simulados
│
├── services/                       # Encapsula lógica de comunicación con fuentes externas
│   ├── apiClient.js                # Configuración base de cliente HTTP (axios, fetch, etc.)
│   ├── [entidad]Service.js         # CRUD de la entidad en una API real
│   ├── authService.js              # Funciones para login, registro, logout
│   └── …                           # Otros servicios relacionados con entidades o integraciones
│
├── utils/                          # Funciones utilitarias, esquemas, validadores
│   ├── constants.js                # Constantes globales del proyecto (estados, rutas, claves, etc.)
│   ├── schemas/                    # Esquemas para construir formularios dinámicos
│   │   └── [entidad]Schema.js      # Esquema del formulario de la entidad
│   ├── validators/                 # Validadores de campos o lógica de negocio
│   │   └── [entidad]Validation.js  # Validación personalizada para la entidad
│   └── formatters.js               # Funciones para formatear fechas, monedas, strings, etc.
│   └── …                           # Otros helpers reutilizables
│
├── styles/                         # Estilos globales y configuración de Tailwind
│   ├── tailwind.css                # Importación y configuración base de Tailwind CSS
│   └── globals.css                 # Estilos globales adicionales del proyecto
│   └── …                           # Otras hojas de estilo si se requiere
│
├── assets/                         # Archivos estáticos accesibles desde código
│   └── logo.svg                    # Logo de la aplicación
│   └── …                           # Íconos, fuentes, imágenes, etc.
│
├── pages/                          # Vistas agrupadas por ruta (React Router o Next.js)
│   ├── login.jsx                   # Vista de login
│   ├── dashboard.jsx              # Dashboard principal de la app
│   └── …                           # Otras páginas generales
│   └── [entidad]/                  # Páginas relacionadas a una entidad
│       ├── index.jsx              # Vista listado principal
│       ├── nuevo.jsx              # Formulario para crear nuevo registro
│       ├── editar.jsx             # Formulario para editar un registro existente
│       └── detalle.jsx            # Vista detalle de un registro individual
│       └── …                      # Otras vistas específicas
│
├── routes/                         # Sistema de rutas de la app
│   └── AppRoutes.jsx              # Archivo central de definición de rutas
│   └── …                          # Rutas protegidas, rutas dinámicas, etc.
│
├── App.jsx                         # Punto de entrada principal del componente raíz de React
└── main.jsx                        # Inicialización de la app, render del DOM



🎯 OBJETIVO DEL PROMPT UNIVERSAL

Genera un componente profesional en React llamado `[NombreDelComponente]`, que utilice datos simulados desde `useMock('[entidad]')`.
El componente debe ser limpio, modular, reusable, y listo para migrar a una API real sin necesidad de reescribir la UI.

📦 ESTRUCTURA DE ARCHIVOS ESPERADA

/components/[NombreDelComponente]/
├── index.jsx         → Contiene solo JSX, sin lógica de datos.
/components/[NombreDelComponente]/styles.js
    → Estilos del componente usando Tailwind, separar styles de componentes (hacer componentes tontos)
/hooks/useMock[Entidad].js
    → Hook con lógica de datos simulados basado en /mocks/[entidad].js.
/mocks/[entidad].js → Datos simulados centralizados para esa entidad.

📋 REGLAS DE GENERACIÓN (APLICABLE A CUALQUIER COMPONENTE)

1. ❌ No incluyas datos hardcodeados en el JSX.
2. ✅ Los datos deben obtenerse exclusivamente desde `useMock('[entidad]')`.
3. ✅ Toda lógica de negocio, filtros, paginación, validación, etc., debe ir dentro de hooks personalizados.
4. ✅ El componente debe recibir props explícitas y configurables como: `data`, `columns`, `title`, `schema`, `actions`, `layout`, `isOpen`, `onClose`, etc.
5. ✅ La UI debe estar completamente desacoplada de la lógica: `index.jsx` solo renderiza.
6. ✅ Si el componente crece más de 300–400 líneas, divídelo en subcomponentes dentro de la misma carpeta.
7. ✅ Usa Tailwind CSS o `styles.js` para los estilos. No uses estilos en línea.
8. ✅ Los estilos deben aplicarse con Tailwind o en `styles.js`, **no inline**.
9. ✅ El componente debe permitir una fácil migración a API real reemplazando `useMock` por `use[Entidad]Api`, manteniendo el mismo contrato de datos.

📘 REQUISITOS DEL HOOK `useMock[Entidad]`

- Importa datos desde `/mocks/[entidad].js`.
- Expone el estado de los datos y funciones como:

```js
const {
  data,          // Datos simulados
  loading,       // Estado de carga
  filters,       // Filtros activos
  setFilters,    // Modificador de filtros
  create,        // Crear nuevo dato
  update,        // Actualizar dato
  remove         // Eliminar dato
} = useMockEntidad();
```
