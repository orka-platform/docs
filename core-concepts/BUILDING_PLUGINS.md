# Building Plugins

## Prerequisites
- Go 1.18+
- Go modules
- Git

### 1) Create a module
```bash
mkdir my-orka-plugin
cd my-orka-plugin
go mod init github.com/yourusername/my-orka-plugin
```

### 2) Add SDK
```bash
go get github.com/orka-platform/orka-plugin-sdk
```

### 3) Implement entrypoint
```go
package main

import (
    sdk "github.com/orka-platform/orka-plugin-sdk"
)

// OrkaCall is the exported entrypoint
func OrkaCall(req sdk.Request, res *sdk.Response) error {
    switch req.Method {
    case "HelloWorld":
        name, _ := req.Args["name"].(string)
        if name == "" {
            name = "World"
        }
        *res = sdk.Response{
            Success: true,
            Data: map[string]any{"message": "Hello, " + name + "!"},
        }
        return nil
    default:
        *res = sdk.Response{
            Success: false,
            Error: "Unknown method: " + req.Method,
        }
        return nil
    }
}
```

### 4) Build
```bash
go build -buildmode=plugin -o myplugin.so .
```

## SDK Contract
- **Request**: `Method` (string), `Args` (map[string]any)
- **Response**: `Success` (bool), optional `Error` (string), optional `Data` (any)

## Supported Function Signatures
- Primary symbol: `OrkaCall(sdk.Request, *sdk.Response) error`
- Fallback symbol: `CallMethod` variants:
  - `func(context.Context, sdk.Request) (sdk.Response, error)`
  - `func(sdk.Request) (sdk.Response, error)`
  - `func(sdk.Request, *sdk.Response) error`

## Plugin Configuration
**Repository layout**
- `main.go` (exports `OrkaCall` or `CallMethod`)
- `config.json` (metadata/method definitions)
- `go.mod`, `go.sum`

**config.json example**
```json
{
  "name": "my-plugin",
  "version": "v0.1.0",
  "description": "A simple example plugin",
  "tags": ["example", "demo"],
  "methods": {
    "HelloWorld": {
      "description": "Returns a greeting message",
      "args": [{"name":"name","type":"string","description":"Name to greet","required":false}],
      "returns": [{"name":"message","type":"string","description":"The greeting message"}]
    }
  }
}
```

**Engine registration (services/engine/config/plugins.json)**
```json
[
  {
    "name": "telegram",
    "version": "v0.1.0",
    "repo": "https://github.com/orka-platform/orka-telegram-plugin.git",
    "service": "TelegramPlugin"
  }
]
```

On startup the engine:
1) Clones repo into `$HOME/.orka/plugins/<name>` or `.../<name>@<version>`  
2) Builds with `go build -buildmode=plugin -o <name>.so`  
3) Loads the shared object and finds the entrypoint  
4) Reads `config.json` for method metadata

> Registering **custom in‑house plugins** is available only for **enterprise, self‑hosted** deployments, due to the single‑tenancy model in the engine. Other users can use the official plugin set and may submit plugins for review to be included in the marketplace.
