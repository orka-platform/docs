---
title: 'Building Plugins'
icon: 'puzzle'
---

### Prerequisites

* Go programming language (1.18+)
* Basic understanding of Go modules
* Git for version control

#### Step 1: Create a new Go module

```bash
mkdir my-orka-plugin
cd my-orka-plugin
go mod init github.com/yourusername/my-orka-plugin
```

#### Step 2: Add the Orka Plugin SDK dependency

```bash
go get github.com/orka-platform/orka-plugin-sdk
```

#### Step 3: Implement the plugin entrypoint

Create a main.go file with the following structure:

```go
package main

import (
    sdk "github.com/orka-platform/orka-plugin-sdk"
)

// OrkaCall is the exported entrypoint for the plugin
func OrkaCall(req sdk.Request, res *sdk.Response) error {
    switch req.Method {
    case "HelloWorld":
        name, _ := req.Args["name"].(string)
        if name == "" {
            name = "World"
        }
        *res = sdk.Response{
            Success: true,
            Data: map[string]any{
                "message": "Hello, " + name + "!",
            },
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

#### Step 4: Build the plugin

```bash
go build -buildmode=plugin -o myplugin.so .
```

### SDK Contract

Plugins use the `github.com/orka-platform/orka-plugin-sdk` package to define the request and response types:

* Request fields:
  * `Method` (string): The logical operation, e.g., SendMessage
  * `Args` (map\[string]any): Input arguments for the method
* Response fields:
  * Success (bool): Whether the operation succeeded
  * Error (string, optional): Error message if the operation failed
  * Data (any, optional): Response data (map or scalar)

### Supported Function Signatures

The plugin loader supports multiple function signatures:

1. Primary Symbol: OrkaCall
   1. `func(sdk.Request, *sdk.Response) error (RPC-style)`
2. Fallback Symbol: CallMethod
   1. `func(context.Context, sdk.Request) (sdk.Response, error)` (context-aware)
   2. `func(sdk.Request) (sdk.Response, error)` (context-free)
   3. `func(sdk.Request, *sdk.Response)` error (RPC-style)

### Plugin Configuration

#### Repository Layout

A typical plugin repository should have the following structure:

* main.go: Defines your plugin with exported `OrkaCall` or `CallMethod` function
* `config.json`: Human-facing metadata and method definitions
* `go.mod`, `go.sum`: Go module files

#### Metadata Configuration (config.json)

The `config.json` file provides metadata about your plugin and its methods:

```json
{
  "name": "my-plugin",
  "version": "v0.1.0",
  "description": "A simple example plugin",
  "tags": ["example", "demo"],
  "methods": {
    "HelloWorld": {
      "description": "Returns a greeting message",
      "args": [
        {
          "name": "name",
          "type": "string",
          "description": "Name to greet",
          "required": false
        }
      ],
      "returns": [
        {
          "name": "message",
          "type": "string",
          "description": "The greeting message"
        }
      ]
    }
  }
}
```

This metadata is used by the Engine and UI to display information about your plugin and its methods.

### Registering Plugins with the Engine

Plugins are registered with the engine through the services/engine/config/plugins.json file:

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

Configuration fields:

* `name` (string, required): Used as the binary name after build
* `repo` (string, required): Git URL for the plugin repository
* `version` (string, required): If present, the Engine namespaces the cache directory and registry key
* `service` (string, required): Service name for the plugin

When the engine starts, it:

1. Clones the plugin repository to `$HOME/.orka/plugins/<name>` or `$HOME/.orka/plugins/<name>@<version>`
2. Builds the plugin with `go build -buildmode=plugin -o <name>.so` .
3. Loads the shared object and looks for the exported entrypoint
4. Reads the plugin's `config.json` to populate method metadata

<mark style="color:yellow;">**Please note that the ability to register custom, internally developed plugins is reserved exclusively for enterprise customers with a self-hosted, on-premise deployment under an enterprise contract. This restriction exists because custom plugins operate under a single-tenancy model within the Orka engine, and therefore cannot be registered in shared, multi-tenant environments.**</mark>

For all other users, Orka provides a rich set of officially supported plugins that can be readily used in workflows.

<mark style="color:blue;">In addition, developers have the opportunity to contribute by submitting their own plugins for review and potential inclusion in Orka’s official plugin marketplace.</mark>



Here you can check a sample LLM plugin: [https://github.com/orka-platform/orka-llm-plugin](https://github.com/orka-platform/orka-llm-plugin).