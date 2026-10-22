# Esquemas de respuesta de la API

Este repositorio contiene esquemas JSON (*JSON Schemas*) para validar las respuestas de la
[API pública de configuración de emisiones](https://bs-d.arag.es/soadev/api-emision-configuracion/publico/v1).

## Esquemas y archivos de ejemplo

| Solicitud | Esquema | Respuestas de ejemplo y parámetros de solicitud |
| --- | --- | --- |
| `GET productoCombicodConsulta` | [`schemas/get_producto_combicod.schema.json`](schemas/get_producto_combicod.schema.json) | [`test/get_producto_combicod.schema.json/`](test/get_producto_combicod.schema.json/): [ES00300](test/get_producto_combicod.schema.json/get_producto_combicod_ES00300.json), [ES04600](test/get_producto_combicod.schema.json/get_producto_combicod_ES04600.json); [parámetros de solicitud y rutas](test/get_producto_combicod.schema.json/params.md) |

Los archivos de ejemplo son muestras de respuestas asociadas a un esquema. Su propiedad `$schema` apunta al esquema con el que deben validarse.
La carpeta de pruebas (*test*) de cada esquema debe contener algunos ejemplos representativos de respuestas, así como un archivo `params.md` que describa cómo realizar las solicitudes correspondientes. Incluye los parámetros de solicitud necesarios para reproducir el ejemplo, pero no incluyas tokens, credenciales ni ningún otro tipo de información confidencial.

## Convención de nombres y carpetas

- Nombra los archivos de esquema utilizando el método HTTP seguido de un nombre breve y descriptivo de la solicitud, en formato *snake case* (minúsculas con guiones bajos) y con el sufijo `.schema.json`:
  `<método>_<descripción_de_la_solicitud>.schema.json` (por ejemplo, `get_producto_combicod.schema.json`).
- Crea una carpeta dentro de `test/` con el nombre exacto del archivo de esquema, incluyendo su sufijo `.schema.json`. - Coloca los ejemplos de respuesta y un archivo `params.md` en esa carpeta. Asigna nombres a los ejemplos que permitan identificar la solicitud y el valor específico correspondiente, como por ejemplo un código de producto.
- Utiliza el mismo nombre para la solicitud tanto en el esquema como en la carpeta de pruebas y en los nombres de los archivos de ejemplo; de este modo, será más sencillo localizar los archivos relacionados.

## Validar una respuesta en VS Code

Añade una propiedad `$schema` a un archivo de respuesta JSON y asígnale la ruta relativa hacia el esquema. Por ejemplo, desde un archivo JSON ubicado en la carpeta de pruebas de dicho esquema:

```json
{
  "$schema": "./../../schemas/get_producto_combicod.schema.json"
}
```

VS Code utilizará el esquema JSON (JSON Schema) referenciado para realizar la validación y señalar cualquier problema detectado en el archivo JSON.