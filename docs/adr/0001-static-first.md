# ADR 0001: Static by default, dynamic opt-in

**Status:** Accepted

## Context
Dynamic checks require launching MCP servers, which executes untrusted code on the scanning machine.

## Decision
The default scan is static only (config parsing). `--connect` is opt-in. It launches servers in a subprocess with a timeout and a scrubbed environment (no inherited secrets beyond what the config specifies), and it never calls tools, only `initialize` and `tools/list` / `prompts/list` / `resources/list`.

## Consequences
CI runs are safe by default. Description-level checks need an explicit flag, and the docs say so.
