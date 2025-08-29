# Wait Node

Pauses execution for a specified duration.

## Core Functionality
- Delay execution precisely
- Build time‑based sequences
- Implement retry backoffs
- Throttle/rate‑limit
- Preserve variables and context during wait

## Properties
- **Unit**: second | minute | hour
- **Value**: positive integer

### Execution Duration Quota
Ensure your wait fits within your plan’s max execution duration, otherwise the run fails.
