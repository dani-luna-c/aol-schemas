# API response schemas

This repository contains JSON Schemas for validating responses from the
[public emission configuration API](https://bs-d.arag.es/soadev/api-emision-configuracion/publico/v1).

## Schema and sample files

| Request | Schema | Sample responses and request parameters |
| --- | --- | --- |
| `GET productoCombicodConsulta` | [`schemas/get_producto_combicod.schema.json`](schemas/get_producto_combicod.schema.json) | [`test/get_producto_combicod.schema.json/`](test/get_producto_combicod.schema.json/): [ES00300](test/get_producto_combicod.schema.json/get_producto_combicod_ES00300.json), [ES04600](test/get_producto_combicod.schema.json/get_producto_combicod_ES04600.json); [request parameters and paths](test/get_producto_combicod.schema.json/params.md) |

The sample files are response examples associated with the schema. Their
`$schema` property points to the schema they are intended to validate against.
Each schema's test folder should contain a couple of representative response
samples and a `params.md` file describing how to make the corresponding
requests. Include request parameters needed to reproduce a sample, but do not
include tokens, credentials, or other secrets.

## Naming and folder convention

- Name schema files using the HTTP method followed by a short, descriptive
  request name, in lowercase snake case, and the `.schema.json` suffix:
  `<method>_<request_description>.schema.json`
  (for example, `get_producto_combicod.schema.json`).
- Create a folder under `test/` with the exact schema filename, including its
  `.schema.json` suffix.
- Put response samples and a `params.md` file in that folder. Name samples to
  identify the request and the relevant sample value, such as a product code.
- Use the same request name in the schema, test folder, and sample filenames so
  related files are easy to find.

## Validate a response in VS Code

Add a `$schema` property to a JSON response file and set it to the relative
path of the schema. For example, from a JSON file in this schema's test folder:

```json
{
  "$schema": "./../../schemas/get_producto_combicod.schema.json"
}
```

VS Code will use the referenced JSON Schema to provide validation and report
problems in the JSON file.
