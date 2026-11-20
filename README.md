# POO_Java_TF_Gr2

Tarea final de Programación Orientada a Objetos. Parte 2: implementación.

Universidad Autónoma de Occidente. Docente: Sandra Lucía Guañarita Fernández.

## Equipo

- Jordy Alejandro Catamuscay
- Samuel Vergara Palacios
- Joshua David Angulo Murillo
- Andrey Valencia Samboni
- Jhoana Valentina Flor Otalora

## Qué hace el aplicativo

Gestiona los proyectos que desarrolla una organización para sus clientes:
registro de proyectos, consultas, administración del equipo de trabajo,
cambio de estado y persistencia en archivos de objetos.

## Estructura

El proyecto tiene dos paquetes, como lo exige el enunciado.

**Modelo**

| Clase | Descripción |
|---|---|
| `Cliente` | Clase abstracta. Datos comunes a todo cliente. |
| `PersonaNatural` | Clase final. Cliente de tipo persona natural. |
| `Empresa` | Clase final. Cliente de tipo empresa, contiene un `Contacto`. |
| `Contacto` | Persona de contacto de una empresa. |
| `Empleado` | Empleado de la organización: gerente o integrante del equipo. |
| `Proyecto` | Clase principal. Contiene un cliente, un gerente y un equipo. |

**Vista**

| Clase | Descripción |
|---|---|
| `UsaProyecto` | Ventana `JFrame` con el formulario de registro y las 18 operaciones. |

### Componentes gráficos utilizados

Son los cinco que se trabajaron en clase, más los paneles contenedores:
`JPanel`, `JLabel`, `JTextField`, `JComboBox`, `JButton` y `JTextArea`.

La ventana tiene tres paneles:

1. Datos del proyecto: campos de texto para el código (lo genera el sistema),
   el título, la fecha de inicio y la duración, más un combo para la unidad
   de duración y los botones Registrar proyecto y Limpiar.
2. Operaciones: combo con las 18 operaciones restantes y los botones
   Ejecutar y Salir.
3. Resultados: área de texto donde se muestran las consultas.

Cada botón tiene su propio método privado `actionPerformed` nombrado como
el botón: `jBotonRegistrarActionPerformed`, `jBotonEjecutarActionPerformed`,
`jBotonLimpiarActionPerformed` y `jBotonSalirActionPerformed`.

Los datos del cliente, del gerente y de los integrantes del equipo se
solicitan con `JOptionPane` porque son demasiados campos para un solo
formulario.

## Elementos de POO aplicados

- **Generalización**: `Cliente` es abstracta y de ella heredan `PersonaNatural` y `Empresa`.
- **Sobreescritura**: cada subclase de `Cliente` reescribe `toString()`.
- **Sobrecarga**: `Proyecto` tiene dos constructores, uno con equipo y otro sin equipo.
- **Asociación simple**: `Proyecto` contiene un `Cliente` y un `Empleado` gerente; `Empresa` contiene un `Contacto`.
- **Asociación múltiple**: `Proyecto` contiene un `ArrayList<Empleado>` como equipo.
- **Polimorfismo en ejecución**: `instanceof` sobre `suCliente` para filtrar por tipo de cliente.
- **Serialización**: todas las clases del modelo implementan `Serializable` para los archivos de objetos.

## Reglas de negocio implementadas

| Elemento | Regla |
|---|---|
| `codigo` | Formato `aaaa-nnn`. El consecutivo reinicia en 1 cada año. Ej. `2026-001`. |
| `titulo` | Entre 20 y 100 caracteres. |
| `fechaInicio` | Formato `aaaa-mm-dd`. |
| `unidadDuracion` | `semanas`, `meses` o `años`. |
| `duracionEstimada` | Semanas 1 a 3. Meses 1 a 11, 13 a 23, 25 a 35. Años 1 a 3. |
| `suEquipo` | Puede quedar vacío al registrar y llenarse después. |
| `estado` | Por defecto `INICIADO`. Otros: `EN CURSO`, `CANCELADO`, `FINALIZADO`, `SUSPENDIDO`, `APLAZADO`. |

Los valores 12, 24 y 36 meses se rechazan a propósito, porque equivalen
a 1, 2 y 3 años y para eso existe la unidad `años`.

## Archivos de objetos

| Archivo | Contenido |
|---|---|
| `datosProyectos` | Todos los proyectos registrados. |
| `datosClientes` | El cliente de cada proyecto. Al leerlos no se repiten. |

Se generan en la carpeta del proyecto. El aplicativo muestra la ruta
completa cuando los crea.

## Cómo ejecutarlo

1. Abrir el proyecto en Apache NetBeans.
2. Clic derecho sobre el proyecto, `Run`.

La clase principal es `Vista.UsaProyecto`.

## Cómo correr las pruebas

Clic derecho sobre el proyecto, `Test Project`.

Las pruebas usan JUnit 4, que NetBeans trae incorporado. Si pide agregar
la biblioteca, se acepta.

Ver `PRUEBAS.md` para el detalle y los resultados.
