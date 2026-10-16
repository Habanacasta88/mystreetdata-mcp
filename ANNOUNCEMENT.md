# Introducing MyStreetData USA MCP: street context for AI assistants

MyStreetData now offers a free, read-only MCP endpoint for exploring a snapshot of 1,334,459 street records across 241 areas in eight US states. Connect a compatible native assistant to https://mystreetdata.com/api/mcp using Streamable HTTP; no account or API key is required.

Start with the coverage tool, find a state-qualified area, then search streets by prefix. The five tools support coverage discovery, area and street search, contextual lookup and comparisons of two to five records. A useful first prompt is: “Check MyStreetData coverage, find Los Angeles in California, and look for streets beginning with Sunset. Explain what the available metrics can and cannot tell me.”

The service returns three carefully scoped contextual measures: EPA’s 2021 block-group National Walkability Index assigned by centroid, observed SNAP retailer counts within 805 metres and observed AFDC EV station counts within 1,609 metres. These are contextual observations, not a street audit, live charger availability or a recommendation about where someone should live. Unknown values remain null, and state-bounded counts can miss neighbours across a border.

This release covers eight states, not the entire USA. Free access has shared capacity limits: 30 tool calls per minute and 100 per day per origin, with 1,000 per day globally. Browser-hosted cross-origin clients are unsupported.

[Connection guide and examples](README.md) · [Service documentation and sources](https://mystreetdata.com/mcp/) · [MyStreetData](https://mystreetdata.com/)

Published by the MyStreetData project team. This repository shares connection metadata and documentation; the hosted server implementation is not included.
