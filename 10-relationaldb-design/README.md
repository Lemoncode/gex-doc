# Proyecto GEX - Definicion Modelo Relacional

## `Introduccion`

Se propone la creacion de un Gestor Electronico de Expedientes de Contratacion, el cual permite la gestion de los contratos publicos de la **Administracion General del Estado y sus Organismos Autonomos,** con el fin de disponer de toda la informacion y documentacion contractual de la administracion de forma unificada.

## `Objetivo`

El objetivo que se busca es formular un diseño de base de datos funcional que de soporte al Gestor de Expedientes de Contratacion. El diseño de base de datos a desarrollar no esta especificado para una tecnologia de base de datos relacional en particular. Asi tambien, se hace uso de requerimientos funcionales para el diseño de una base de datos relacional, la cual deriva en la formulacion y mapeo de entidades a tablas y atributos a campos, estableciendo relaciones entre entidades a traves de identificadores unicos en forma de llaves.

## `Requisitos Funcionales`

Se revisan los videos **_00-Propuesta-A.mp4_** y **_01-Propuesta-B.mp4_**, donde se explica en genral el sistema gestor actual y las expectativas sobre el nuevo sistem. A continuacion se definen alguns marcadores de tiempo, que se refieren a las partes del video donde se da una explicacion del uso de la aplicacion, los cuales son tomados como referencia para la definicion de requisitos funcionales.

### _Ref: 00-Propuesta-A:_

`[01:35 - 04:16] Explicacion general de las vistas y sus elementos.`

- Marcadores:
  - `02:10: Explicacion de los tipos de Expedientes "Nuevos"`

`[04:16 - 04:47] Propuesta de endpoints de la aplicacion --Sitemap.`

`[04:48 - 05:50] Ejemplo de un expediente en formato json.`

`[05:51 - 12:50] Propuesta y descripcion de pantallas generales.`

- Marcadores:
  - `06:45: Vista parcial de los atributos de un expediente`
  - `07:48: Atributos de Datos Generales`
  - `08:21: Atributos de Datos Economicos`
  - `09:13: Atributos de Certificaciones --Cardinalidad 1 a *`
  - `09:51: Atributos de Notas --Cardinalidad 1 a *`
  - `11:17: Revision formulario creacion de expedientes --Multi Steps --Ejemplo: Nueva Prorroga`

`[12:51 - 16:42] Revision de la base de datos actual (MS Access).`

- Marcadores:
  - `13:30: Se permiten campos nulos? --ver: Estado`
  - `13:50: Ejemplo de filtrado de expedientes`
  - `14:51: Visualizacion de expediente`
  - `14:45: Vista Datos Generales`
  - `14:49: Vista Certificaciones`
  - `15:01: Vista Notas`
  - `15:29: Vista Contactos > Empresas`

`[16:45 - 19:15] Revision de la base de datos nueva (MS Access).`

### _Ref: 01-Propuesta-B:_

`[03:45 - 13:30] Explicacion del ciclo de vida de un expediente y sus estados.`

## `Entidades y Atributos`

### _Expedientes_

- \_id
- clase_id
- descripcion
- numero_expediente
- numero_soroalla2
- estado_id
- periodo_ejecucion
- periodo_inicio
- periodo_final
- unidad_id
- pre_base_importe
- pre_base_importe_iva
- pre_iva_porcentaje
- pre_iva_importe
- adj_base_importe
- adj_base_importe_iva
- adj_iva_porcentaje
- adj_iva_importe
- empresa_id
- usuario_id
- ts_creado
- dt_modificado

### _Expediente_Clases_

- \_id
- clase
- tipo

### _Expediente_Estados_

- \_id
- nombre

### _Estados_de_Expediente_

- expediente_id
- estado_id
- timestamp

### _Documentos_

- \_id
- nombre
- descripcion

### _Documentos_de_Expediente_

- expediente_id
- documento_id
- url

### _Unidades_

- \_id
- nombre

### _Anualidades_

- \_id
- ejercicio
- aplicacion_presupuestaria
- importe
- expediente_id

### _Certificaciones_

- \_id
- factura_numero
- factura_fecha
- periodo_inicio
- periodo_final
- importe
- ts_creado
- usuario_id
- expediente_id

### _Notas_

- \_id
- contenido
- ts_creado
- usuario_id
- expediente_id

### _Empresas_

- \_id
- CIF
- nombre
- direccion
- sector
- web

### _Contactos_

- \_id
- nombre
- apellidos
- telefono_movil
- telefono_fijo
- email
- comentarios
- empresa_id

### _Usuarios_

- \_id
- nombre
- apellidos
- contraseña
- email
- rol

## `Diagrama Entidad Relacion`

**_Referirse a: `./GEX_ERD_R0.drawio`_**
