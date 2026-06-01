# SBOM Analyser

A browser-based Software Bill of Materials (SBOM) analysis tool for reviewing dependency quality, license risk, vulnerabilities, component age, and overall SBOM health.

## Overview

SBOM Analyser is a client-side HTML application that parses CycloneDX and SPDX JSON SBOMs and provides:

- License compliance and risk analysis
- CVE analysis using OSV
- Component age and latest-version checks
- SBOM structural quality checks
- NTIA minimum element gap analysis
- Executive summary scoring and export

Privacy-first design:
- All parsing and analysis runs locally in the browser
- Only package identifiers needed for optional live lookups are sent to public registries/APIs
- No SBOM document is uploaded to an application server

## Current feature set

### Executive Summary
- SBOM Health Score (0–100)
- Risk cards for:
  - high-risk licenses
  - outdated components
  - critical/high CVEs
  - NTIA gaps
- Recommended actions
- DOCX summary export
- “Fetch All Missing Data” workflow when downstream analysis is incomplete

### SBOM Overall Quality
- SBOM metadata cards:
  - SBOM name
  - format
  - spec version
  - tool
- Structural quality cards:
  - unique components
  - duplicate components
  - NTIA passing components
  - NTIA gaps
- NTIA / quality issue breakdown with sub-tabs for:
  - all gaps
  - missing component name
  - missing version
  - missing supplier
  - missing PURL
  - invalid PURL syntax
- Shared quality issue table
- Duplicate component detection based on normalized `name + version`
- PURL syntax validation

Note:
- The quality issue counts are currently based on issue instances across categories, not deduplicated components. A single component can contribute more than one issue.

### License Analysis
- License categorization:
  - permissive
  - caution / weak copyleft
  - critical / strong copyleft
  - non-commercial
  - unknown
- Unknown-license retrieval from supported public registries
- Inline retrieval guidance and apply flow
- CSV export

### CVE Analysis
- OSV-based vulnerability lookup
- Severity filtering:
  - critical
  - high
  - medium
  - low
  - unknown
  - manual review
- CVE summary text in the table
- CSV export

### Component Age Analysis
- Registry-based release date lookup
- Latest version and latest release date retrieval
- Age-band classification
- EOL / archived repository handling where supported
- CSV export

PyPI note:
- PyPI age lookup now uses the package-level JSON API and derives release dates from the `releases` map.
- PyPI package names are normalized using a PEP 503-style approach and can use the PURL-derived package name when present.

## Supported formats

- CycloneDX JSON
  - 1.2
  - 1.3
  - 1.4
  - 1.5
  - 1.6
- SPDX JSON
  - 2.2
  - 2.3

## Getting started

### Prerequisites
- A modern browser such as Chrome, Edge, Firefox, or Safari
- Internet access for optional registry/API lookups

### Usage
1. Open `SBOM Analyser.html` in a browser.
2. Load an SBOM by:
   - choosing a JSON file, or
   - pasting JSON into the input area.
3. Run analysis.
4. Review:
   - Executive Summary
   - SBOM Overall Quality
   - License Analysis
   - CVE Analysis
   - Component Age
5. Optionally fetch:
   - unknown licenses
   - CVEs
   - component ages
6. Export:
   - DOCX summary report
   - CSVs from detailed tabs

## Health score

The health score is weighted as follows:

```text
Health Score =
  (License Score × 30%) +
  (Age Score × 25%) +
  (CVE Score × 30%) +
  (NTIA Score × 15%)
```

### Inputs
- License Score: proportion of components without high-risk license findings
- Age Score: proportion of components not classified as outdated/EOL
- CVE Score: proportion of components without critical/high CVEs
- NTIA Score: proportion of components without NTIA minimum-element gaps

### Ratings

| Score | Rating |
|---|---|
| 80–100 | Excellent |
| 60–79 | Good |
| 40–59 | Fair |
| 0–39 | Needs Improvement |

## Data sources

- License metadata:
  - PyPI
  - npm
  - GitHub
  - crates.io
  - NuGet
  - Maven Central
- Vulnerabilities:
  - OSV
- Component age / release metadata:
  - PyPI
  - npm
  - crates.io
  - NuGet
  - Go proxy / pkg.go.dev
  - GitHub
  - Maven Central

## Privacy and security

- Client-side processing only
- HTTPS-based public registry/API access
- No secret storage in the app
- No SBOM upload to a backend service
- Browser/network policy still applies for CORS, TLS trust, and public API availability

## Performance notes

Recent updates include:
- reduced repeated full-table re-renders during batch fetches
- capped large CVE and Age table rendering to improve responsiveness
- improved large-SBOM handling with stress-test fixtures

Current limitation:
- large datasets can still be expensive because the app is a single-file client-side renderer and some views still rebuild full table markup.

## Limitations

- JSON SBOM input only
- Public registry coverage varies by ecosystem and package quality
- Some packages require manual review
- Public APIs may rate-limit or return incomplete metadata
- Browser TLS/CORS environment can affect live retrieval
- Large SBOMs may still be slow in some views

## NTIA checks currently implemented

The quality view currently checks these component-level minimum fields:
- component name
- version
- supplier
- unique identifier (PURL)

Note:
- The README previously implied broader NTIA checks such as dependency relationships, author, and timestamp. The current quality table logic is focused on the component-level fields above.

## Architecture

- Single-file HTML application
- HTML/CSS/JavaScript
- IBM Carbon-inspired dark UI
- DOCX export via docx.js
- Native browser APIs for parsing, rendering, and network access

## Contributing

1. Update `SBOM Analyser.html`
2. Test with representative CycloneDX and SPDX JSON files
3. Re-test:
   - summary scoring
   - quality tab counts/sub-tabs
   - license retrieval
   - CVE retrieval
   - age retrieval
4. Update `README.md` when behavior changes

## License

Add the project license here.

## Support

Open an issue or document the problem with:
- SBOM format/version
- affected ecosystem(s)
- browser/version
- console/network errors if live retrieval is involved

---

**Version**: 1.0
**Last Updated**: 2026-05-29