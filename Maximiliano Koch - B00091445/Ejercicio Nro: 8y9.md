# Ejercicio 8 y 9
## Enunciado
https://docs.google.com/document/d/13AiC7tsTU7WvUa87QHYiJH6z77UvyhpxUS9NQ65lT4o/edit?usp=sharing

## Resolución
# 1. Análisis de Requerimientos:
Ejercicio 1

Requisitos Funcionales (Lo que el sistema debe hacer):
- El sistema debe permitir registrar un nuevo producto ingresando su nombre, descripción, precio, categoría y stock inicial.
- El sistema debe permitir editar y eliminar productos existentes.
- El sistema debe mostrar un listado con el inventario actual actualizado en tiempo real.
- El sistema debe permitir buscar productos por nombre o filtrar por categoría.
- El sistema debe generar una alerta visual cuando el stock de un producto llegue a un nivel mínimo predefinido.

Requisitos No Funcionales (Cómo el sistema debe comportarse):
- Seguridad: El sistema debe requerir autenticación (usuario y contraseña) para acceder y realizar modificaciones en el inventario.
- Usabilidad: La interfaz debe ser responsiva, adaptándose correctamente tanto a computadoras de escritorio como a teléfonos móviles.
- Rendimiento: Las búsquedas en el inventario no deben demorar más de 2 segundos en mostrar los resultados.
- Disponibilidad: La aplicación web debe estar operativa el 99.9% del tiempo.

# Ejercicio 2
1. Caso de Uso: Agregar un nuevo producto

- Actor principal: Administrador del inventario.
- Precondiciones: El administrador debe haber iniciado sesión en la aplicación web de forma exitosa.
- Flujo principal (Éxito):
  1. El administrador hace clic en el botón "Nuevo Producto".
  2. El sistema muestra un formulario vacío.
  3. El administrador ingresa los datos correspondientes (Nombre, Descripción, Precio, Stock Inicial y selecciona la Categoría).
  4. El administrador hace clic en "Guardar".
  5. El sistema valida que los campos obligatorios estén completos y que los formatos sean correctos (ej: precio mayor a 0).
  6. El sistema guarda el producto en la base de datos.
  7. El sistema muestra un mensaje de éxito ("Producto guardado correctamente") y actualiza la lista del inventario.
- Flujos alternativos:
- (Paso 5) Faltan datos o formato incorrecto: El sistema detiene el proceso, muestra un mensaje de alerta indicando qué campo está mal completado y mantiene la información ya ingresada en la pantalla para que el administrador la corrija.

# Ejercicio 3: Elabora un diagrama de flujo de datos para la aplicación web del ejercicio 1.

<img width="443" height="626" alt="image" src="https://github.com/user-attachments/assets/fb672c5f-f623-4c1b-b91a-cdf4fe71a9a0" />

# Ejercicio 4: Diseña la interfaz de usuario para la pantalla de "Inicio" de la aplicación web del ejercicio 1

<img width="1585" height="898" alt="image" src="https://github.com/user-attachments/assets/7f4b3067-3298-4d23-9fa8-6cb64eccb17a" />

# Ejercicio 5: Elige una arquitectura adecuada para la aplicación web del ejercicio 1 y justifica tu elección.

1. Para esta aplicación web de gestión de inventario, la arquitectura más adecuada es una **Arquitectura Cliente-Servidor basada en el patrón MVC (Modelo-Vista-Controlador)**.

**Justificación:**
- **Separación de responsabilidades:** Permite que el diseño de la interfaz (la Vista) evolucione de forma independiente a la lógica de negocio (Controlador) y la base de datos (Modelo).
- **Flexibilidad y Adaptabilidad:** Al separar el Frontend del Backend, se cumple con el requisito no funcional de que la aplicación sea responsiva (adaptable a celulares y PCs) sin tener que reescribir las reglas de inventario.
- **Mantenibilidad:** Evita el código "rígido" o "viscoso" (como vimos en los fundamentos ágiles), asegurando que los futuros cambios solicitados por el cliente sean fáciles de integrar.

Ejercicio 6: Diseña la base de datos para la aplicación web del ejercicio 1.

<img width="837" height="459" alt="image" src="https://github.com/user-attachments/assets/02ad78d8-dbfb-4199-aebb-4c7e7693a0f0" />


# 4. Diseño
### 1. Diagrama de Dominio
**Identifica las entidades, atributos y relaciones del sistema.**

<img width="584" height="616" alt="image" src="https://github.com/user-attachments/assets/f43e9866-ea22-4e26-aedb-43f7313bd752" />

### 2. Diagrama de Robustez
Analiza cómo el sistema responde a diferentes escenarios de uso.

<img width="1055" height="176" alt="image" src="https://github.com/user-attachments/assets/171bed74-be2c-45ed-afa8-8a6339c1e02c" />

### 3. Prototipo

<img width="1585" height="898" alt="image" src="https://github.com/user-attachments/assets/7f4b3067-3298-4d23-9fa8-6cb64eccb17a" />

### 4. Diagrama de Secuencia
Describe la interacción entre los diferentes objetos del sistema.

<img width="1091" height="645" alt="image" src="https://github.com/user-attachments/assets/898bbb18-31b7-420a-aff8-3dfb8d32f6fe" />

### 5. Diagrama de Clases
Define las clases, sus atributos, métodos y relaciones.

<img width="763" height="468" alt="image" src="https://github.com/user-attachments/assets/1a317432-29f5-4a88-bcad-962cd949c530" />

# Ejercicio 7 y 8
1. A continuación se presenta la implementación de la funcionalidad "Agregar un nuevo producto" desarrollada en **Node.js** utilizando el framework **Express**.

```javascript
// productoController.js
const db = require('../config/database'); // Simulación de conexión a la base de datos

const agregarProducto = async (req, res) => {
    // 1. Recibir los datos enviados desde el formulario (Prototipo UI)
    const { nombre, descripcion, precio, stock_inicial, id_categoria, id_usuario } = req.body;

    // Validación básica de campos obligatorios
    if (!nombre || !precio || !stock_inicial || !id_categoria || !id_usuario) {
        return res.status(400).json({ error: "Faltan campos obligatorios para el registro." });
    }

    try {
        // Iniciar transacción para asegurar que Producto y Movimiento se guarden juntos
        await db.query('BEGIN');

        // 2. Validar que la categoría exista (Paso 3 del Diagrama de Secuencia)
        const categoria = await db.query('SELECT id_categoria FROM Categoria WHERE id_categoria = ?', [id_categoria]);
        if (categoria.length === 0) {
            await db.query('ROLLBACK');
            return res.status(404).json({ error: "La categoría especificada no existe." });
        }

        // 3. Guardar el nuevo producto (Paso 5 del Diagrama de Secuencia)
        const queryProducto = `
            INSERT INTO Producto (nombre, descripcion, precio, stock_actual, id_categoria, id_usuario)
            VALUES (?, ?, ?, ?, ?, ?)
        `;
        const resultProducto = await db.query(queryProducto, [nombre, descripcion, precio, stock_inicial, id_categoria, id_usuario]);
        const id_producto_nuevo = resultProducto.insertId;

        // 4. Registrar el movimiento inicial de stock (Paso 7 del Diagrama de Secuencia)
        const queryMovimiento = `
            INSERT INTO Movimiento (fecha, tipo_accion, cantidad, id_producto, id_usuario)
            VALUES (NOW(), 'Alta de Stock Inicial', ?, ?, ?)
        `;
        await db.query(queryMovimiento, [stock_inicial, id_producto_nuevo, id_usuario]);

        // Confirmar los cambios en la base de datos
        await db.query('COMMIT');

        // 5. Responder a la Vista con éxito (Paso 9 del Diagrama de Secuencia)
        return res.status(201).json({
            mensaje: "Producto agregado con éxito",
            producto: {
                id_producto: id_producto_nuevo,
                nombre: nombre,
                stock: stock_inicial
            }
        });

    } catch (error) {
        // Si algo falla, deshacer los cambios
        await db.query('ROLLBACK');
        console.error("Error al guardar el producto:", error);
        return res.status(500).json({ error: "Error interno del servidor al intentar agregar el producto." });
    }
};

module.exports = {
    agregarProducto
};
```
# Ejercicio 9

1. Para la funcionalidad de "Agregar un nuevo producto", definimos el siguiente conjunto de pruebas unitarias utilizando el framework **Jest**. 

Aplicamos los principios de **TDD** y metodologías ágiles, asegurando que cada prueba sea atómica y aislada. Para lograr este aislamiento, utilizamos *mocks* (simuladores) de la base de datos, garantizando que probamos exclusivamente la lógica de negocio del servicio . 

Las pruebas siguen el ciclo estándar: Preparar el estado (Arrange), Ejecutar (Act) y Comprobar (Assert) .

```javascript
// productoService.test.js
const { registrarNuevoProducto } = require('./productoService');
const db = require('../config/database');

// 1. Aislamos la base de datos reemplazándola con un Mock (Simulador)
jest.mock('../config/database');

describe('Suite de Pruebas Unitarias: Agregar un nuevo producto', () => {
    
    // Test 1: Camino feliz (Éxito)
    test('Debería registrar el producto y crear el movimiento si los datos son válidos', async () => {
        // Arrange (Preparar estado)
        const mockDatos = {
            nombre: 'Monitor 24"', descripcion: 'Monitor LED', 
            precio: 150000, stock_inicial: 10, id_categoria: 1, id_usuario: 1
        };
        // Simulamos que la BD responde que la categoría "1" existe y el insert es exitoso
        db.getConnection.mockResolvedValue({
            beginTransaction: jest.fn(),
            query: jest.fn()
                .mockResolvedValueOnce([[{ id_categoria: 1 }]]) // 1er Query: validación categoría
                .mockResolvedValueOnce([{ insertId: 99 }])      // 2do Query: insert producto
                .mockResolvedValueOnce([{}]),                   // 3er Query: insert movimiento
            commit: jest.fn(),
            release: jest.fn()
        });

        // Act (Ejecutar)
        const resultado = await registrarNuevoProducto(mockDatos);

        // Assert (Comprobar)
        expect(resultado.exito).toBe(true);
        expect(resultado.producto.id_producto).toBe(99);
        expect(resultado.producto.stock_inicial).toBe(10);
    });

    // Test 2: Falla regla de negocio (Precio inválido)
    test('Debería rechazar la operación si el precio es menor o igual a cero', async () => {
        // Arrange
        const mockDatosInvalidos = {
            nombre: 'Mouse', precio: -500, stock_inicial: 5, id_categoria: 1, id_usuario: 1
        };

        // Act & Assert
        await expect(registrarNuevoProducto(mockDatosInvalidos))
            .rejects.toThrow("El precio debe ser mayor a cero.");
    });

    // Test 3: Falla de integridad (Categoría inexistente)
    test('Debería ejecutar un ROLLBACK si la categoría indicada no existe', async () => {
        // Arrange
        const mockDatos = {
            nombre: 'Teclado', precio: 25000, stock_inicial: 5, id_categoria: 999, id_usuario: 1
        };
        const mockConexion = {
            beginTransaction: jest.fn(),
            query: jest.fn().mockResolvedValueOnce([[]]), // BD simulada devuelve lista vacía (no encontró la categoría)
            rollback: jest.fn(),
            release: jest.fn()
        };
        db.getConnection.mockResolvedValue(mockConexion);

        // Act & Assert
        await expect(registrarNuevoProducto(mockDatos))
            .rejects.toThrow("La categoría indicada no existe en el catálogo.");
        
        // Verificamos que el sistema haya cancelado la transacción en la BD
        expect(mockConexion.rollback).toHaveBeenCalled(); 
    });
});
```
# Ejercicio 10
Ejecuta pruebas de integración para la funcionalidad de "Agregar
un nuevo producto" en la aplicación web del ejercicio 1.
```javascript
    // producto.integration.test.js
    const request = require('supertest');
    const app = require('../app'); // Nuestra aplicación Express
    const db = require('../config/database');

    describe('Pruebas de Integración: Agregar un nuevo producto', () => {
    
    // 1. Crear un estado de comienzo definido (Configuración especial del entorno) [2]
    beforeAll(async () => {
        // Nos conectamos a la base de datos de pruebas y limpiamos registros viejos
        await db.query('DELETE FROM Movimiento');
        await db.query('DELETE FROM Producto');
        // Insertamos una categoría base para cumplir con la integridad de la llave foránea
        await db.query('INSERT INTO Categoria (id_categoria, nombre_categoria) VALUES (1, "Electrónica")');
    });

    // 4. Limpiar los recursos al finalizar [2]
    afterAll(async () => {
        await db.query('DELETE FROM Categoria WHERE id_categoria = 1');
        await db.end(); 
    });

    test('Debería insertar un producto en la BD y generar su historial de movimiento', async () => {
        const datosProducto = {
            nombre: 'Notebook', descripcion: 'Notebook 15 pulgadas', 
            precio: 850000, stock_inicial: 5, id_categoria: 1, id_usuario: 1
        };

        // 2. Ejecutar código de prueba: Hacemos la petición real HTTP que atravesará todas las capas [2]
        const response = await request(app)
            .post('/api/productos')
            .send(datosProducto);

        // 3. Comprobar que el estado final se corresponde con el esperado [2]
        // A. Verificamos la respuesta de la API
        expect(response.status).toBe(201);
        expect(response.body.exito).toBe(true);

        // B. Verificamos la integración real con la Base de Datos
        const [productoBD] = await db.query('SELECT * FROM Producto WHERE nombre = "Notebook"');
        expect(productoBD.length).toBe(1);
        expect(productoBD.stock_actual).toBe(5);

        // C. Verificamos que el componente del historial (Movimiento) haya actuado correctamente
        const [movimientoBD] = await db.query('SELECT * FROM Movimiento WHERE id_producto = ?', [productoBD.id_producto]);
        expect(movimientoBD.length).toBe(1);
        expect(movimientoBD.tipo_accion).toBe('Alta de Stock Inicial');
    });
    });
  ```
# Ejercicio 11: Definir un plan de despliegue para la aplicación web del ejercicio 1.
A continuación se define el plan de despliegue para la aplicación web de gestión de inventario, integrando prácticas ágiles y herramientas DevOps:

Modelo de distribución: Aplicación web en Internet, lo que permite un despliegue inmediato garantizando que todos los administradores usen siempre la última versión disponible del sistema

Control de Versiones: El código fuente se mantendrá centralizado en un repositorio de Git (GitHub).

Entornos definidos:
Staging (Pre-producción): Entorno de pruebas idéntico al real.

Producción: El servidor definitivo donde el cliente utilizará el sistema.
Pipeline de Integración y Entrega Continua (CI/CD): Se implementará un flujo automatizado (utilizando herramientas como Jenkins o GitHub Actions). Al integrar nuevo código en la rama principal, el pipeline deberá:
Ejecutar automáticamente las pruebas unitarias y de integración (Jest) definidas en la fase anterior.
Si las pruebas pasan al 100%, empaquetar (build) la aplicación.
Desplegar (deploy) la nueva versión en el servidor de producción.

Rollback: En caso de que se detecte un defecto crítico en producción, el sistema de control de versiones permitirá volver a la compilación estable anterior de manera inmediata

# Ejercicio 12: Despliega la aplicación web del ejercicio 1 en un servidor de producción

Resolución
Para cumplir con el despliegue del sistema Node.js en un servidor de producción, se ejecutaron los siguientes pasos utilizando una plataforma de alojamiento en la nube (PaaS) para aplicaciones web:

### Pasos de despliegue ejecutados:

Configuración de Variables: Se crearon las variables de entorno en el servidor de producción (ej. DB_HOST, DB_USER, DB_PASSWORD) para mantener seguras las credenciales de la base de datos sin subirlas al repositorio público.

Despliegue de Base de Datos: Se aprovisionó un servidor de base de datos relacional (MySQL) en la nube y se ejecutaron los scripts (DDL) correspondientes al Ejercicio 6 para crear las tablas Usuario, Categoria, Producto y Movimiento.

Sincronización de Código: Se enlazó la rama principal (main) del repositorio de GitHub con la plataforma de alojamiento.

Arranque: Se configuraron los comandos de compilación (npm install) e inicio (npm start) para levantar la API del inventario.

# Ejercicio 13: Definir un plan de mantenimiento para la aplicación web del ejercicio 1.

### Mantenimiento Preventivo (Reducción de Deuda Técnica):

Refactorización Continua: Siguiendo las prácticas de XP, el equipo tiene la responsabilidad compartida de mejorar, limpiar y ordenar el código continuamente sin cambiar su comportamiento externo. Esto garantiza que el sistema sea fácil de mantener a futuro.

Integración Continua: Se mantendrá un servidor de integración que ejecute la suite completa de pruebas unitarias y de integración automáticamente con cada nuevo cambio, previniendo errores de regresión.

### Mantenimiento Correctivo (Resolución de Bugs):

Análisis de Causa Raíz (Técnica de los 5 Por Qués): Cuando se reporte un error en producción, el equipo no aplicará un "parche" rápido. Se utilizará el principio Lean de "Optimizar el todo" aplicando la técnica de los 5 Whys para encontrar el verdadero origen del fallo en el proceso o en el código y solucionarlo de raíz.

Corrección guiada por pruebas (TDD): Todo bug reportado se traducirá primero en un Test Automatizado que falle (Fase Roja). Luego se escribirá el código para solucionarlo (Fase Verde) y se refactorizará (Fase Azul). De esta forma, el error queda documentado y se evita que vuelva a ocurrir.

# Ejercicio 14: Implementa una corrección de errores para un problema detectadoen la aplicación web del ejercicio 1.

Problema detectado (Bug): Durante el uso de la aplicación, se detectó que el sistema permite ingresar productos con el mismo nombre exacto, lo que está rompiendo el módulo de búsquedas del inventario.

Corrección implementada: Aplicando las reglas del TDD (Test-Driven Development), primero creamos un test que reprodujo el error intentando guardar un producto duplicado. Luego, actualizamos la capa de Servicio (productoService.js) agregando una nueva Regla de Negocio para validar que el nombre sea único en la Base de Datos antes de insertarlo.

```javascript
// productoService.js (VERSIÓN CORREGIDA)
const db = require('../config/database');

const registrarNuevoProducto = async (datosProducto) => {
    const { nombre, descripcion, precio, stock_inicial, id_categoria, id_usuario } = datosProducto;

    if (precio <= 0) throw new Error("El precio debe ser mayor a cero.");
    if (stock_inicial < 0) throw new Error("El stock inicial no puede ser negativo.");

    let conexion;
    try {
        conexion = await db.getConnection();
        await conexion.beginTransaction();

        // [CORRECCIÓN DE BUG]: Validar que no exista un producto con el mismo nombre
        const [productoExistente] = await conexion.query('SELECT id_producto FROM Producto WHERE nombre = ?', [nombre]);
        if (productoExistente.length > 0) {
            throw new Error("Ya existe un producto registrado con ese nombre en el inventario.");
        }

        const [categoria] = await conexion.query('SELECT id_categoria FROM Categoria WHERE id_categoria = ?', [id_categoria]);
        if (categoria.length === 0) {
            throw new Error("La categoría indicada no existe en el catálogo.");
        }

        // Guardar el producto
        const queryProducto = `
            INSERT INTO Producto (nombre, descripcion, precio, stock_actual, id_categoria, id_usuario) 
            VALUES (?, ?, ?, ?, ?, ?)
        `;
        const [resultProducto] = await conexion.query(queryProducto, [nombre, descripcion, precio, stock_inicial, id_categoria, id_usuario]);
        
        // Generar historial de movimiento
        if (stock_inicial > 0) {
            const queryMovimiento = `
                INSERT INTO Movimiento (fecha, tipo_accion, cantidad, id_producto, id_usuario) 
                VALUES (NOW(), 'Alta de Stock Inicial', ?, ?, ?)
            `;
            await conexion.query(queryMovimiento, [stock_inicial, resultProducto.insertId, id_usuario]);
        }

        await conexion.commit();
        return { exito: true, mensaje: "Producto registrado correctamente" };

    } catch (error) {
        if (conexion) await conexion.rollback();
        throw error;
    } finally {
        if (conexion) conexion.release();
    }
    };

    module.exports = { registrarNuevoProducto };
  ```
### Ejercicio 15

Fase 1: Definición del Equipo (Roles de Scrum)
Para cumplir con el marco ágil, el equipo de 3 a 5 personas se divide de la siguiente manera:

Product Owner: Encargado de entender las necesidades del negocio de construcción de galpones y definir qué funcionalidades tienen más valor.

Scrum Master: Facilitador que organizará la reunión y guiará al equipo para que las historias se redacten de forma clara siguiendo el formato ágil.

Development Team (Equipo de Desarrollo): Propondrán las soluciones técnicas y estimarán la complejidad de cada historia.

Fase 2: Planificación (Sprint Planning)

El equipo realiza una sesión de planificación para estructurar el Product Backlog. Se decide enfocar este primer ciclo en las funcionalidades principales requeridas: creación de presupuestos, inclusión de etapas y generación de informes.

Fase 3: Creación de las Historias de Usuario (Product Backlog)

A continuación, el equipo redactó las siguientes tres historias principales aplicando las buenas prácticas (criterios INVEST) y definiendo sus criterios de aceptación o condiciones de satisfacción:

Historia de Usuario 1: Creación de presupuesto detallado
Descripción: Como vendedor de la constructora, quiero generar un presupuesto detallado ingresando los materiales y dimensiones del galpón, para poder enviarle una cotización precisa al cliente final.
Criterios de Aceptación:
El sistema debe tener un formulario que permita ingresar: dimensiones (ancho, largo, alto) y tipo de material (chapa, estructura metálica).
El sistema debe calcular el costo total de los materiales automáticamente de acuerdo a los precios actualizados de la base de datos.
El sistema debe sumar automáticamente el porcentaje de impuestos (IVA) al costo final.

Historia de Usuario 2: Inclusión de etapas de construcción
Descripción: Como jefe de obra, quiero dividir el presupuesto total del galpón en etapas de construcción (cimientos, estructura, cerramiento), para poder organizar los hitos de pago con el cliente.
Criterios de Aceptación:
El usuario debe poder crear hasta 5 etapas de obra distintas dentro de un mismo presupuesto.
El sistema debe permitir asignar un porcentaje de cobro a cada etapa.
El sistema debe validar obligatoriamente que la suma de los porcentajes de todas las etapas sea exactamente el 100% antes de guardar.

Historia de Usuario 3: Generación de informes
Descripción: Como cliente comprador, quiero poder descargar mi presupuesto en formato digital, para poder imprimirlo, revisarlo fuera del sistema y compararlo.
Criterios de Aceptación:
Debe existir un botón claramente visible de "Descargar Informe PDF" en la vista del presupuesto terminado.
El documento generado debe incluir obligatoriamente el logo de la constructora, la fecha de emisión y el plazo de validez de la oferta.
El informe debe mostrar el desglose total de costos por etapas.

Fase 4: Revisión (Sprint Review)
Al finalizar, el equipo presentará estas tarjetas de historias de usuario frente a los interesados (el resto de la clase)
, explicando el contexto de negocio de la construcción de galpones y cómo cada criterio de aceptación garantiza que se construya lo que el cliente realmente necesita.
