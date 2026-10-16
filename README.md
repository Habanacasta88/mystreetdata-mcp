# MyStreetData USA MCP

Search US street records and retrieve sourced walkability, SNAP retailer and EV station context from an AI assistant.

**Free hosted endpoint:** https://mystreetdata.com/api/mcp  
**Transport:** Streamable HTTP · Read-only · No account or API key  
**Documentation:** https://mystreetdata.com/mcp/

This repository contains public connection metadata and documentation. It does not contain the hosted server implementation or a downloadable dataset.

## Connect

For Claude Code:

```sh
claude mcp add --transport http mystreetdata-usa https://mystreetdata.com/api/mcp
```

For native clients supporting this configuration format, use [.mcp.json](.mcp.json). Other clients can add the endpoint as a remote Streamable HTTP server. Browser-hosted cross-origin clients are unsupported. The endpoint was tested with the official MCP SDK using protocol 2025-11-25; client-specific interfaces are not independently certified.

## Five tools

| Tool | Purpose |
| --- | --- |
| `mystreetdata_get_coverage` | Check available states, record counts, sources and limitations. |
| `mystreetdata_search_areas` | Find state-qualified areas by prefix. |
| `mystreetdata_search_streets` | Find street records by prefix within an area. |
| `mystreetdata_get_street_context` | Retrieve identity and three contextual metrics. |
| `mystreetdata_compare_streets` | Compare two to five records on supported dimensions. |

Example request: “Use MyStreetData to check coverage, find Los Angeles in California and search for streets beginning with Sunset. Explain the sources and limitations before comparing any records.”

The snapshot contains **1,334,459 street records in 241 state-qualified areas across 8 US states**. It does not cover the entire United States. Area labels come from site slugs and are not an official gazetteer. Search uses prefixes, returns at most 10 results per page and supports pagination.

## Interpreting the data

- **EPA National Walkability Index:** the 2021 block-group index (1–20), assigned using a street centroid. It is not a street-level audit.
- **SNAP:** observed participating retailer count within 805 metres.
- **AFDC:** observed EV station count within 1,609 metres, not connectors or live availability.

Counts are state-bounded and may miss nearby locations across state borders. Unknown values stay null. Local extraction dates do not establish the source edition. Street links are supplied only when the corresponding page file was verified; this does not establish search-engine indexing.

The MCP does not provide property prices, crime or school socioeconomic scores, protected demographic attributes, individual business names, or housing recommendations. Source definitions and caveats accompany the data; see the [service documentation](https://mystreetdata.com/mcp/).

## Availability and limits

30 tool calls/minute and 100/day per origin; 1,000/day globally. The anonymous shared quota can be exhausted by other users. HTTP rate limits also apply. Requests are limited to 16 KiB and responses to 32 KiB. Access is read-only, with no arbitrary SQL, URL fetching or filesystem access.

## Support and licensing

Use this repository’s issues for connection or documentation problems. Do not include credentials or personal information. The MIT license covers only the original metadata and documentation in this repository; it does not license the hosted implementation or underlying source datasets. The service documentation identifies the sources and their applicable terms.

Official MCP Registry identifier: `io.github.Habanacasta88/mystreetdata`.
