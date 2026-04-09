# SBOM Version Drift Analyzer

A comprehensive, privacy-focused tool for analyzing Software Bill of Materials (SBOM) files with advanced license risk assessment, component age tracking, version drift detection, and EOL/deprecated package identification.

## 🔒 Privacy First

**All analysis happens locally in your browser.** Your SBOM data—including company names, package names, versions, and license information—never leaves your device. The only external calls are optional registry lookups (PyPI, npm, etc.) that send only individual package names to retrieve license and release date information.

## ✨ Features

### 1. **License Analysis**
- Automatic license risk classification (High Risk, Caution, Permissive, Unknown)
- Non-commercial license detection (CC-BY-NC, BUSL, PolyForm NC, etc.)
- Proprietary vs. third-party component identification
- **Package URL (PURL) display** - Shows purl in brackets next to each package name
- Detailed license implications and recommendations
- Interactive filtering and search

### 2. **Live License Retrieval**
- Automated license lookup from public registries:
  - PyPI (Python)
  - npm (JavaScript/Node.js)
  - crates.io (Rust)
  - NuGet (.NET)
  - GitHub repositories
  - Go modules
- Batch processing with progress tracking
- Apply retrieved licenses back to your analysis

### 3. **Component Age & Version Drift Analysis**
- **Full Maven Central support** for release date and version tracking
- Release date tracking from public registries:
  - npm (JavaScript/Node.js)
  - PyPI (Python)
  - Maven Central (Java/Maven)
  - crates.io (Rust)
  - NuGet (.NET)
  - Go proxy (Go modules)
  - GitHub repositories
- Six age categories:
  - **Fresh**: < 1 year old
  - **Aging**: 1-2 years old
  - **Stale**: 2-3 years old
  - **Critical**: 3+ years old
  - **Dormant**: At latest version but 3+ years old (unmaintained)
  - **EOL**: End of Life / Deprecated packages
- Visual age distribution dashboard
- Latest version comparison and outdated dependency detection
- Archived repository detection (GitHub)

### 4. **EOL/Deprecated Detection**
Automatically identifies deprecated and end-of-life components from:
- **CycloneDX properties**: Detects `internal:deprecated`, `internal:deprecation_reason`, and EOL markers
- **Known EOL database**: Hardcoded list of common EOL packages (e.g., log4j 1.x, moment.js)
- **Example detection**:
  ```json
  {
    "name": "log4j",
    "version": "1.2.17",
    "properties": [
      {"name": "internal:deprecated", "value": "true"},
      {"name": "internal:deprecation_reason", "value": "EOL; vulnerable per log4shell PoC"}
    ]
  }
  ```

## 🚀 Getting Started

### Installation

No installation required! This is a standalone HTML file that runs entirely in your browser.

1. Download the `sbom-Version_Drift_Analyzer.html` file
2. Open it in any modern web browser (Chrome, Firefox, Safari, Edge)
3. That's it!

### Usage

1. **Upload Your SBOM**
   - Drag and drop your SBOM file onto the upload area, or click to browse
   - Supported formats: CycloneDX JSON (v1.2-v1.6), SPDX JSON (v2.2-v2.3)

2. **Review License Analysis**
   - View the automatic risk classification
   - Filter by risk level, license type, or origin
   - Search for specific packages
   - Click any row for detailed license information

3. **Retrieve Missing Licenses** (Optional)
   - Switch to the "Live Retrieval" tab
   - Click "Retrieve all" to fetch licenses from public registries
   - Review and apply found licenses

4. **Analyze Component Age** (Optional)
   - Switch to the "Component Age" tab
   - Click "Fetch all ages" to retrieve release dates
   - View age distribution and identify outdated dependencies
   - Export results to CSV

5. **Export Results**
   - Download updated SBOM with retrieved licenses
   - Export CSV reports for further analysis

## 📊 Supported SBOM Formats

### CycloneDX
- Versions: 1.2, 1.3, 1.4, 1.5, 1.6
- Format: JSON
- Component types: library, application, framework, container, etc.

### SPDX
- Versions: 2.2, 2.3
- Format: JSON
- Package information with license data

## 🎨 User Interface

Built with IBM's Carbon Design System for a professional, accessible experience:
- Dark theme optimized for extended use
- Responsive layout for desktop and mobile
- Keyboard navigation support
- Clear visual hierarchy and status indicators

## 🔍 License Risk Categories

### High Risk (Red)
Strong copyleft licenses that may require source disclosure:
- GPL, AGPL, EUPL
- May require releasing your source code under the same license

### Caution (Orange)
Weak copyleft licenses with specific obligations:
- LGPL, MPL, CDDL
- Review use case carefully; some obligations apply

### Permissive (Green)
Minimal restrictions, attribution may be required:
- MIT, Apache, BSD, ISC
- Generally safe for commercial use

### Non-Commercial (Purple)
Restricted or prohibited commercial use:
- CC-BY-NC, BUSL, PolyForm Noncommercial
- Consult legal counsel before commercial use

### Unknown (Gray)
License not identified or absent from SBOM:
- Use Live Retrieval to fetch missing licenses
- Manual investigation may be required

## 🛠️ Technical Details

### Supported Ecosystems for Age Data Fetching

**Fully Supported** (automatic release date and latest version retrieval):
- **Python** (PyPI) ✓
- **JavaScript/Node.js** (npm) ✓
- **Java/Maven** (Maven Central) ✓ 
- **Rust** (crates.io) ✓
- **.NET** (NuGet) ✓
- **Go** (Go proxy) ✓
- **GitHub** repositories ✓

**Limited/Manual Support**:
- **Ruby** (RubyGems) - Manual lookup required
- Other ecosystems - Manual investigation needed

### Browser Requirements
- Modern browser with JavaScript enabled
- ES6+ support (Chrome 51+, Firefox 54+, Safari 10+, Edge 15+)
- No server or backend required

### File Size Limits
- Recommended: < 10 MB SBOM files
- Large SBOMs (1000+ components) may take longer to process

## 📝 CSV Export Format

Component Age CSV includes:
- Package name and version
- Ecosystem
- Release date and age (in days)
- Age band classification
- Latest version and release date

## 🔐 Security & Privacy

- **No data transmission**: All SBOM processing happens locally in your browser
- **No tracking**: No analytics or telemetry
- **No storage**: Files are not saved or cached
- **Limited external calls**: Only for optional registry lookups
  - Only package name and version are sent to public registries
  - Supported registries: npm, PyPI, Maven Central, crates.io, NuGet, Go proxy, GitHub
  - No SBOM structure or company data is transmitted
  - All external calls use HTTPS

## 📄 License

This tool is provided as-is for SBOM analysis purposes.

## 🤖 Built with BOB

This tool was created with assistance from BOB, an AI-powered development assistant.
