---
title: 'Plugins'
description: 'Extend Orka with custom functionality without modifying the core engine.'
icon: 'puzzle'
---

### Introduction

Orka's plugin system allows you to extend the platform with custom functionality without modifying the core engine. Plugins are loaded as shared objects (.so) directly into the Orka Engine process, eliminating the need for separate plugin processes. This approach offers several benefits:

* Lower resource usage: Plugins run in the same process as the engine
* Faster startup time: No need to start separate processes
* Reduced latency: No inter-process communication overhead
* Improved reliability: Fewer moving parts and failure points

Plugins enable you to integrate with external services (e.g., Telegram, Slack, CRM systems, payment gateways) or implement custom business logic that can be reused across multiple workflows.

### Plugin Architecture

Orka uses an in-process plugin architecture where plugins are:

1. Written in Go and compiled as shared objects (.so)
2. Loaded directly into the Orka Engine process at startup
3. Executed via direct function calls when triggered by workflow nodes

The plugin system consists of these main components:

* Plugin Host: Central service that manages all plugins
* Plugin Loader: Responsible for loading plugins from .so files
* Plugin Manager: Handles the lifecycle of plugins (cloning, building, caching)
* Plugin Executor: Executes plugin functions within workflows

