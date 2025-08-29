# HTTP Request Node

Makes HTTP calls to external APIs/services. Response data can be mapped into variables.

## Core Functionality
- GET/POST/PUT/DELETE/PATCH/HEAD/OPTIONS
- Headers & body (JSON/form/raw)
- Auth: none, basic, header, bearer
- Response mapping (extract fields, store whole body with `$`)
- Timeout

## Properties
- **Method** — HTTP verb
- **URL** — full URL, path/query params, supports `{{var}}` interpolation
- **Headers** — custom headers
- **Body** — JSON/form/raw; `{{var}}` interpolation
- **Send Body** — boolean
- **Auth** — none | basic | header | bearer
- **Response Mapping** — field extraction / whole body
- **Timeout** — ms
