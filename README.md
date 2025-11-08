## OpenAPI Discriminator Validation Issue

This repository demonstrates that neither **Spectral** nor **Vacuum** properly validate the presence of `discriminator.propertyName` in schema properties.

### Problem

According to the [OpenAPI 3.1.2 specification](https://spec.openapis.org/oas/v3.1.2.html#discriminator-object), the property referenced in discriminator must be present in the schema properties (although it can be optional starting from OpenAPI 3.2).

> The expectation now is that a property with name petType MUST be present in the response payload, and the value will correspond to the name of a schema defined in the OpenAPI Description. Thus the response payload:

**Test file:** [`api.yaml`](./api.yaml) - OpenAPI 3.0.3 spec with invalid discriminator

**Both linters fail to detect when discriminator references a non-existent property:**

- [spectral-issue/](./spectral-issue/) - No discriminator validation rules
- [vacuum-issue/](./vacuum-issue/) - Has `oas2-discriminator` but lacks `oas3-discriminator`