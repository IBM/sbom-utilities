# SBOM Quality Insights

A comprehensive web-based tool for analyzing and validating CycloneDX Software Bill of Materials (SBOM) files. This application provides detailed insights into SBOM quality, compliance with NTIA minimum requirements, and automated fixes for common issues.

## Features

### 📊 Overview Dashboard
- **SBOM Metadata**: View basic information including format, version, serial number, and timestamps
- **Component Statistics**: Total components, unique suppliers, and license distribution
- **Quality Indicators**: Visual status indicators for NTIA compliance, dependency validation, and PURL quality
- **Quick Insights**: At-a-glance view of potential issues and areas requiring attention

### 🔍 Detailed Analysis

#### 1. Components Not Meeting NTIA Criteria
Identifies components that fail to meet NTIA's minimum elements for SBOM:
- **Author/Supplier Name**: Missing component author or supplier information
- **Component Name**: Missing or invalid component names
- **Version**: Missing version information
- **Unique Identifier**: Missing PURL, CPE, or other unique identifiers
- **Dependency Relationships**: Missing or incomplete dependency information

**Features:**
- Summary statistics showing count of components failing each criterion
- Detailed table with component-level breakdown
- Collapsible sections for easy navigation

#### 2. Dependency Validation
Validates the integrity of dependency relationships in the SBOM:
- **Duplicate Refs**: Detects multiple dependency entries with the same ref
- **Duplicate dependsOn Values**: Identifies duplicate values within dependsOn arrays

**Features:**
- Automatic fix capability that merges duplicate dependencies
- Preview changes before applying
- One-click download of corrected SBOM
- Detailed statistics on dependency structure

#### 3. Components with Generic PURL
Identifies components using generic Package URLs (pkg:generic/):
- Generic PURLs lack specific package manager context
- May prevent accurate vulnerability matching in security scanners
- Affects CVE mapping and security analysis

**Features:**
- Complete list of components with generic PURLs
- Explanation of security implications
- Detailed component information including name, version, and full PURL

#### 4. Components with only a GitHub PURL and no CPE
Detects components that:
- Use GitHub PURLs (pkg:github/) referencing source repositories
- Lack CPE (Common Platform Enumeration) identifiers
- May not be properly matched in vulnerability databases

**Features:**
- Statistics showing total components and CPE coverage
- Explanation of why CPE identifiers matter for CVE mapping
- Detailed component listing with PURL information

#### 5. Library and Framework Components
Comprehensive view of all library and framework components:
- Filters out application and operating-system type components
- Shows complete component details including licenses
- Useful for dependency auditing and license compliance

### 🛠️ Automated Fixes

#### Dependency Fix
- **Merges duplicate dependency entries** with the same ref
- **Deduplicates dependsOn arrays** to ensure unique values
- **Preserves all unique dependencies** while removing redundancy
- **Preview mode** to review changes before applying
- **One-click download** of corrected SBOM

## Usage

### Getting Started
1. Open `sbom_quality_insights.html` in a modern web browser
2. Click "Choose File" or drag-and-drop your CycloneDX SBOM JSON file
3. The application will automatically analyze and display results

### Supported Formats
- **CycloneDX JSON** (versions 1.2, 1.3, 1.4, 1.5, 1.6)
- File must be valid JSON format
- Must contain CycloneDX SBOM structure

### Navigation
- **Overview Tab**: High-level summary and quality indicators
- **Analysis Tab**: Detailed findings organized by validation type
- **Raw Data Tab**: View the original SBOM JSON with syntax highlighting

### Applying Fixes
1. Navigate to the Analysis tab
2. Locate the "Dependency Validation" section
3. Click "Preview Changes" to review proposed fixes
4. Click "Apply Fixes & Download" to download the corrected SBOM
5. The fixed SBOM will be downloaded with "_fixed" appended to the filename

## Technical Details

### Architecture
- **Single-file application**: All HTML, CSS, and JavaScript in one file
- **Client-side processing**: No server required, all analysis runs in the browser
- **No external dependencies**: Pure vanilla JavaScript
- **Responsive design**: Works on desktop and mobile devices

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with ES6+ support

### Data Privacy
- **100% client-side**: No data is sent to any server
- **No tracking**: No analytics or external requests
- **Secure**: All processing happens locally in your browser

### Performance
- Handles SBOMs with thousands of components
- Instant analysis and validation
- Efficient memory usage with global variable storage
- Optimized table rendering with text wrapping

## Validation Logic

### NTIA Minimum Elements
Based on NTIA's "The Minimum Elements For a Software Bill of Materials (SBOM)" guidance:
- Supplier Name
- Component Name
- Version of the Component
- Other Unique Identifiers (PURL, CPE)
- Dependency Relationship
- Author of SBOM Data
- Timestamp

### Dependency Validation
- Checks for duplicate `ref` values in dependencies array
- Validates uniqueness of values in `dependsOn` arrays
- Ensures referential integrity of dependency relationships

### PURL Quality Checks
- **Generic PURL Detection**: Identifies pkg:generic/ usage
- **GitHub PURL Analysis**: Detects pkg:github/ without CPE
- **CPE Coverage**: Tracks components with CPE identifiers for CVE mapping

## File Structure

```
SBOM Quality Insights/
├── sbom_quality_insights.html    # Main application file
└── README.md                      # This file
```

## Known Limitations

1. **CycloneDX Only**: Currently supports CycloneDX format only (SPDX support planned)
2. **JSON Format**: XML format not supported
3. **Browser Storage**: Large SBOMs (>5MB) use global variables instead of localStorage
4. **Client-side Only**: Requires JavaScript enabled in browser

## Future Enhancements

- SPDX format support
- Additional PURL quality checks
- License compliance validation
- Export reports to PDF
- Batch processing of multiple SBOMs
- Custom validation rules

## Contributing

This is a standalone tool. For issues or feature requests, please contact the maintainer.

## License

[Specify your license here]

## Version History

### Current Version
- NTIA minimum elements validation
- Dependency validation with automatic fixes
- Generic PURL detection
- GitHub PURL without CPE detection
- Library and framework component listing
- Responsive UI with collapsible sections
- Preview and apply fixes functionality

## Support

For questions or issues, please contact the development team.

---

**Note**: This tool is designed to help improve SBOM quality and identify potential issues. It should be used as part of a comprehensive SBOM management strategy, not as the sole validation mechanism.