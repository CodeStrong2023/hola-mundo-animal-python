# Tienda Hola Mundo Animal - Proyecto Integrador

Integrantes:
* Quinteros, Mariana
* Bazán Azargado, Ma. Emilia
* Torres Urzua, Siro Ezequiel
* Esteche, Yamila Eliana
* Balmaceda, Adriana Verónica
* Martinez, Fabricio 
* Juan Beresiarte

## Estructura del código
El código se divide en varias secciones:
1. Definición de modelos de datos (clases Producto y Compra)
2. Definición de una clase Query para interactuar con la base de datos
3. Definición de una clase TypedQuery que hereda de Query y agrega métodos específicos para interactuar con los modelos de datos
4. Definición de funciones auxiliares para realizar operaciones específicas (e.g. elegir código postal, agregar producto, validar tarjeta de débito)
5. Definición de la función main que inicia el programa y llama a las funciones auxiliares
6. Definición de la función init_db que crea la base de datos y carga datos iniciales

## Modelos de Base de Datos

![grafica_base_de_datos](/base_de_datos.png)

#### Producto

- **Atributos**:
  - `id`: Identificador único del producto.
  - `nombre`: Nombre del producto.
  - `precio`: Precio del producto.
  - `cantidad_disponible`: Cantidad disponible en inventario.
  - `cantidad_comprada`: Cantidad comprada por los clientes.

#### Compra

- **Atributos**:
  - `id`: Identificador único de la compra.
  - `nombre_cliente`: Nombre del cliente que realizó la compra.
  - `direccion_cliente`: Dirección de entrega del cliente.
  - `localidad`: Localidad de entrega.
  - `costo_total`: Costo total de la compra.
  - `pago_realizado`: Estado del pago.
  - `producto_id`: ID del producto comprado (clave foránea).

## Clases y Métodos de Consulta

### `Query`

- **Métodos**:
  - `get_all(model)`: Retorna todos los registros de un modelo.
  - `get_by_id(model, id)`: Retorna un registro por su ID.
  - `get_one(model, **kwargs)`: Retorna el primer registro que cumple con los filtros.
  - `add(instance)`: Agrega una nueva instancia a la base de datos.
  - `update()`: Guarda los cambios realizados en la sesión.
  - `delete(instance)`: Elimina una instancia de la base de datos.
  - `filter_by(model, **kwargs)`: Retorna registros que cumplen con los filtros especificados.
  - `execute_raw_query(raw_query)`: Ejecuta una consulta SQL en crudo.
  - `close_session()`: Cierra la sesión actual.

### `TypedQuery`

- **Métodos Específicos**:
  - `obtener_productos()`: Retorna todos los productos.
  - `obtener_compras()`: Retorna todas las compras.
  - `obtener_producto(**kw)`: Retorna un producto que cumpla con los filtros especificados.
  - `obtener_compra(**kw)`: Retorna una compra que cumpla con los filtros especificados.
  - `registrar_compra(**kw)`: Registra una nueva compra en la base de datos.

## Clases Auxiliares

- `CompraActual`: Almacena temporalmente los detalles de la compra actual.

## Funciones Auxiliares

- `elegir_codigo_postal(matriz)`: Permite al usuario seleccionar un código postal para calcular el costo de envío.
- `agregar_producto(productos)`: Permite al usuario agregar un producto al carrito de compras.
- `validar_tarjeta_debito()`: Valida y procesa el pago mediante tarjeta de débito.
- `mostrar_mensaje_despedida()`: Muestra un mensaje de despedida al usuario.

## Observaciones y propuestas de mejora sobre el Proyecto
1. La función init_db carga datos iniciales en la base de datos, pero el codigo no proporciona una forma gráfica de agregar nuevos productos o editar los existentes.
2. La función validar_tarjeta_debito no realiza una validación real de la tarjeta de débito, solo pide al usuario que ingrese los datos y los guarda en la base de datos.
3. El código utiliza la biblioteca tkinter para crear una interfaz gráfica de usuario, pero no proporciona una forma de interactuar con la interfaz.
