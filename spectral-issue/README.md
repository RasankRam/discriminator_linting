## Problem

The `../api.yaml` contains an invalid discriminator - property `petType` is referenced but not defined:

```yaml
Pet:
  type: object
  properties:
    name:
      type: string
    age:
      type: integer
  discriminator:
    propertyName: petType  # ERROR: petType not in properties
```

According to [OpenAPI 3.1.2 spec](https://spec.openapis.org/oas/v3.1.2.html#discriminator-object), this property must be defined in the schema's properties.

After linting, it passes without errors. Possible expected error: something like `discriminator property 'petType' is not defined`.
