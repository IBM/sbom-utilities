# SBOM Dependency Analyzer

A **pure frontend** web application that analyzes CycloneDX SBOMs to clearly distinguish between **direct dependencies** and **transitive dependencies**. No backend server required!

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![No Dependencies](https://img.shields.io/badge/dependencies-none-green.svg)
![Pure Frontend](https://img.shields.io/badge/frontend-HTML%2FJS%2FCSS-blue.svg)

## 🌟 Features

- 🔍 **Analysis Insights Tab**: Deep-dive explanations of SBOM structure, dependency relationships, and quality assessment
- 📊 **Clear Visualization**: Color-coded cards showing direct (green) vs transitive (orange) dependencies
- 🎯 **SBOM Quality Assessment**: Automatic detection of well-structured vs flat inventory SBOMs
- 📋 **Structural Analysis**: Detailed breakdown of components and dependencies sections
- 🔄 **Drag & Drop Upload**: Simply drag and drop your SBOM file to analyze it
- 🔍 **Search & Filter**: Search by component name/group and filter by component type
- 📈 **Summary Statistics**: Quick overview of total components and dependency breakdown
- 🎨 **Modern UI**: Clean, responsive interface with smooth animations
- 📦 **Dependency Graph**: Shows which components depend on others
- 🚀 **Zero Setup**: Single HTML file - just open and use!
- 🔒 **Privacy First**: All processing happens in your browser - no data sent to servers

## 📋 Table of Contents

- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [Usage](#usage)
- [Testing with Sample SBOMs](#testing-with-sample-sboms)
- [Deployment Options](#deployment-options)
- [Component Information](#component-information)
- [File Structure](#file-structure)
- [Troubleshooting](#troubleshooting)
- [Browser Support](#browser-support)
- [Contributing](#contributing)

## 🚀 Quick Start

### Option 1: Direct File Open (Easiest)

1. Download or clone this repository
2. Open `index-table.html` in your web browser
3. Upload a CycloneDX SBOM JSON file
4. View the analysis!

That's it! No installation, no dependencies, no server required.

### Option 2: Local Web Server (Recommended for Development)

If you prefer to run it through a web server:

```bash
# Using Python (if installed)
python3 -m http.server 8000
# Then open http://localhost:8000

# Using Node.js (if installed)
npx http-server
# Then open http://localhost:8080

# Using PHP (if installed)
php -S localhost:8000
# Then open http://localhost:8000
```

## 🔍 How It Works

The analyzer uses the CycloneDX SBOM's `dependencies` section to determine:

1. **Direct Dependencies**: Components listed in the main project's `dependsOn` array
2. **Transitive Dependencies**: All other components (dependencies of dependencies)

All processing happens **client-side** in your browser using JavaScript:
- Parses the SBOM JSON file
- Identifies the main component from metadata
- Extracts dependency relationships
- Classifies components as direct or transitive
- Renders the interactive visualization

**No data leaves your computer** - perfect for sensitive or proprietary SBOMs!

## 💻 Usage

### Step 1: Open the Application

Simply open `index-table.html` in any modern web browser (Chrome, Firefox, Safari, Edge).

### Step 2: Upload Your SBOM

- **Click** the upload area, or
- **Drag and drop** a CycloneDX JSON file onto the upload area

Supported format: CycloneDX JSON (`.json`)

### Step 3: View the Analysis

The application displays four main tabs:

#### 📊 Analysis Insights Tab (Default)
The first tab provides a comprehensive analysis of your SBOM structure:

- **SBOM Quality Assessment**: Visual status indicator (✅ Well-Structured, ⚠️ Flat Inventory, or ❌ Incomplete)
- **SBOM Overview**: Format, spec version, main component, and component counts
- **Structure Analysis**:
  - Components section breakdown
  - Dependencies section analysis
  - Main component status
- **Direct Dependencies Explanation**: How they're identified and what they represent
- **Transitive Dependencies Explanation**: How they're traced through the dependency chain
- **Understanding the Results**: Interpretation guide and accuracy assessment

This tab helps you understand:
- Whether your SBOM has proper dependency relationships
- How direct vs. transitive dependencies are determined
- Any structural issues that might affect analysis accuracy
- Recommendations for improving SBOM quality

#### 📦 All Dependencies Tab
Shows all components in the SBOM with detailed information

#### 🟢 Direct Dependencies Tab
Components directly used by your project (green indicators)

#### 🟠 Transitive Dependencies Tab
Indirect dependencies pulled in through the dependency chain (orange indicators)

### Additional Features

- **Summary Cards**: Total components, direct and transitive dependency counts
- **Main Component**: The primary component being analyzed
- **Component Lookup**: Search for specific components by name and version
- **Search Bar**: Find components by name, version, or license
- **Type Filters**: Show/hide libraries, applications, frameworks
- **Sortable Columns**: Click column headers to sort by name, version, risk, etc.
- **Expandable Rows**: Click any row to see detailed dependency information, risk assessment, and NTIA compliance

### Features

- **Search**: Type in the search box to filter components by name or group
- **Filter by Type**: Use checkboxes to show/hide specific component types
- **Tab Navigation**: Switch between direct and transitive dependencies
- **Hover Effects**: Hover over cards for enhanced visibility
- **Responsive Design**: Works on desktop, tablet, and mobile devices

## 🧪 Testing with Sample SBOMs

The repository includes sample SBOM files in the `sample_sboms/` directory for testing:

### Available Samples

1. **sample-cyclonedx-sbom.json** - A basic CycloneDX SBOM example
2. **acme-ecommerce-microservices-sbom.json** - A more complex microservices example

### How to Test

1. Open `index.html` in your browser
2. Navigate to the `sample_sboms/` folder
3. Drag and drop one of the sample files into the upload area
4. Explore the analysis results

These samples demonstrate:
- ✅ Direct vs transitive dependency classification
- ✅ Multiple component types (libraries, applications, frameworks)
- ✅ License information display
- ✅ Dependency relationship visualization
- ✅ Search and filter functionality

## 🌐 Deployment Options

### Option 1: File Sharing (Simplest)

Just share the `index.html` file! Recipients can:
- Download it
- Open it in their browser
- Use it immediately

Perfect for:
- Email attachments
- Shared drives
- USB drives
- Internal wikis

### Option 2: Web Hosting

Host the file on any web server:

**GitHub Pages:**
```bash
# Push to GitHub, then enable GitHub Pages in repository settings
# Access at: https://yourusername.github.io/sbom-dependency-analyzer/
```

**Static Hosting Services:**
- Netlify: Drag and drop the file
- Vercel: Deploy with one command
- AWS S3: Upload as static website
- Azure Static Web Apps: Simple deployment

**Internal Web Server:**
```bash
# Copy to your web server's document root
cp index.html /var/www/html/sbom-analyzer.html

# Access at: http://yourserver/sbom-analyzer.html
```

### Option 3: Intranet Deployment

For corporate environments:

1. **SharePoint**: Upload as a page or web part
2. **Confluence**: Embed using HTML macro
3. **Internal Wiki**: Add as a page
4. **File Server**: Place in a shared folder

### Option 4: Electron App (Optional)

Package as a desktop application:

```bash
# Install Electron
npm install -g electron

# Create package.json and main.js
# Package for distribution
electron-packager . SBOMAnalyzer --platform=all
```

## 📊 Component Information

Each component card displays:

- **Name and Version**: Component identifier
- **Type**: library, application, framework, etc.
- **Group/Namespace**: Package organization
- **PURL**: Package URL for universal identification
- **Licenses**: License information (SPDX IDs or names)
- **Dependencies**: Number of components this depends on
- **Dependency Type**: Direct (green border) or Transitive (orange border)

### Color Coding

- 🟢 **Green border/background**: Direct dependencies
- 🟠 **Orange border/background**: Transitive dependencies
- 🔵 **Blue badge**: Library components
- 🔴 **Pink badge**: Application components
- 🟣 **Purple badge**: Framework components
- ⚪ **Gray badge**: Other component types

## 📁 File Structure

```
sbom-dependency-analyzer/
├── index-table.html        # Enhanced table view with Analysis Insights (recommended)
├── index.html              # Original card view (legacy)
├── README.md               # This file
├── LICENSE                 # License file
├── sample_sboms/           # Example SBOM files for testing
│   ├── sample-cyclonedx-sbom.json
│   └── acme-ecommerce-microservices-sbom.json
├── app.py                  # Legacy Flask backend (optional)
├── requirements.txt        # Legacy Python dependencies (optional)
├── templates/              # Legacy template files (optional)
│   └── index.html
└── static/                 # Legacy static files (optional)
    ├── css/
    │   └── style.css
    └── js/
        └── app.js
```

**Note**:
- **`index-table.html`** is the recommended version with Analysis Insights tab and drag-and-drop support
- **`index.html`** is the original card-based view
- The `app.py`, `requirements.txt`, `templates/`, and `static/` files are from the original Flask-based version and are **not required** for the standalone HTML versions.

## 🔧 Troubleshooting

### File Won't Open

**Issue**: Double-clicking `index-table.html` doesn't work
- **Solution**: Right-click → "Open with" → Choose your browser

### Upload Fails

**Issue**: File upload doesn't work
- ✅ Check file is valid JSON
- ✅ Ensure file is CycloneDX format (has `"bomFormat": "CycloneDX"`)
- ✅ Verify file has `.json` extension
- ✅ Try one of the sample SBOMs to verify the app works

### Analysis Shows No Dependencies

**Issue**: SBOM loads but shows no dependencies
- ✅ Verify SBOM has a `dependencies` section
- ✅ Check SBOM has `metadata.component` defined
- ✅ Ensure SBOM follows CycloneDX specification v1.2+
- ✅ Compare with the sample SBOMs

### Browser Compatibility

**Issue**: Application doesn't work in older browsers
- **Solution**: Use a modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- **Reason**: Uses modern JavaScript features (async/await, ES6+)

### CORS Errors (When Using File Protocol)

**Issue**: Console shows CORS errors
- **Solution**: Use a local web server instead of opening the file directly
- **Alternative**: Most features work fine with file:// protocol despite warnings

### Large SBOM Performance

**Issue**: Application is slow with very large SBOMs (10,000+ components)
- **Solution**: Modern browsers handle this well, but consider:
  - Using search/filters to reduce visible components
  - Closing other browser tabs
  - Using a desktop browser instead of mobile

## 🌐 Browser Support

Works in all modern browsers:

| Browser | Minimum Version | Recommended |
|---------|----------------|-------------|
| Chrome  | 90+            | Latest      |
| Firefox | 88+            | Latest      |
| Safari  | 14+            | Latest      |
| Edge    | 90+            | Latest      |

**Mobile Support**: ✅ Fully responsive and works on mobile devices

**Offline Support**: ✅ Works completely offline once loaded

## 🤝 Contributing

Contributions are welcome! This is a single-file application, making it easy to modify.

### How to Contribute

1. Fork the repository
2. Make your changes to `index-table.html` (recommended) or `index.html`
3. Test with the sample SBOMs
4. Submit a pull request

### Development Tips

- Enhanced version: `index-table.html` (table view with Analysis Insights)
- Original version: `index.html` (card view)
- All code is self-contained (HTML, CSS, JavaScript)
- CSS is in the `<style>` tag
- JavaScript is in the `<script>` tag
- Use browser DevTools for debugging
- Test with various SBOM files (well-structured and flat inventory types)

### Recent Enhancements (v2.1.0)

- ✅ **Analysis Insights Tab**: Comprehensive SBOM structure analysis with educational content
- ✅ **Drag & Drop Upload**: Enhanced file upload with drag-and-drop support
- ✅ **SBOM Quality Assessment**: Automatic detection of structural issues
- ✅ **Deep-dive Explanations**: Clear explanations of direct vs transitive dependencies

### Ideas for Future Enhancements

- Export analysis results to CSV/PDF
- Visualize dependency tree/graph
- Compare two SBOMs
- Support for SPDX format
- Dark mode toggle
- Vulnerability integration
- License compliance checking

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with vanilla JavaScript (no frameworks!)
- Inspired by IBM Carbon Design System
- Supports [CycloneDX](https://cyclonedx.org/) SBOM format
- Created for easy SBOM analysis without infrastructure

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check the troubleshooting section
- Test with the provided sample SBOMs
- Review the browser console for error messages

## 🎯 Use Cases

Perfect for:
- ✅ Quick SBOM analysis without setup
- ✅ Offline/air-gapped environments
- ✅ Sensitive/proprietary SBOMs (no data leaves your machine)
- ✅ Training and demonstrations
- ✅ Integration into existing tools/workflows
- ✅ Sharing with non-technical stakeholders

## 🔄 Version History

- **2.1.0** (2026-04-02)
  - ✨ **NEW: Analysis Insights Tab** - Comprehensive SBOM structure analysis
  - 🔍 Deep-dive explanations of dependency relationships
  - 📊 Automatic SBOM quality assessment (well-structured vs flat inventory)
  - 🎯 Detailed breakdown of components and dependencies sections
  - 💡 Educational content explaining direct vs transitive dependencies
  - 🔄 **NEW: Drag & Drop Upload** - Simply drag SBOM files to analyze
  - 📋 Visual feedback for drag-and-drop operations
  - ⚠️ Identifies structural issues and provides recommendations
  - 🎨 Enhanced UI with color-coded status indicators

- **2.0.0** (2026-03-20)
  - **Pure frontend version** - no backend required!
  - Single HTML file with embedded CSS and JavaScript
  - All processing happens client-side
  - Zero dependencies, zero installation
  - Complete privacy - no data sent to servers
  - Sample SBOMs included for testing

- **1.0.0** (Previous)
  - Flask-based backend version
  - Required Python and server setup

---

**Made with ❤️ for better SBOM analysis**

*No servers, no dependencies, no complexity - just open and analyze!*