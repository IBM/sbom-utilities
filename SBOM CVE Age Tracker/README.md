# CVE Age Tracker

A modern, user-friendly web application for analyzing CVE (Common Vulnerabilities and Exposures) publication dates and tracking their age. Built with IBM Carbon Design System principles.

## Overview

CVE Age Tracker helps security professionals and developers quickly assess the age of vulnerabilities by fetching real-time data from the National Vulnerability Database (NVD) and presenting it in an intuitive, visual format.

## Features

### Core Functionality
- **Bulk CVE Analysis**: Analyze multiple CVEs simultaneously
- **Real-time Data**: Fetches current vulnerability information from NVD API
- **Age Calculation**: Automatically calculates how many days/years old each CVE is
- **Severity Classification**: Displays CVSS severity ratings (Critical, High, Medium, Low)
- **Smart Grouping**: Organizes results by severity level with collapsible sections

### Visualizations
- **Summary Dashboard**: Quick overview with key metrics
  - Total CVEs analyzed
  - Count of CVEs > 6 months old
  - Percentage of old vulnerabilities
  - Count of CVEs < 6 months old
- **Timeline Chart**: Visual representation of CVE distribution over time
  - View by month or quarter
  - Color-coded by severity
  - Interactive tooltips
  - Click to filter by period and severity

### Data Export
- **CSV Export**: Download complete analysis results
- Includes CVE ID, severity, dates, age metrics, and descriptions
- Timestamped filenames for easy organization

### User Experience
- **IBM Carbon Design**: Professional, accessible interface
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Color-Coded Panels**: Visual distinction for different metrics
- **Progressive Loading**: Real-time progress indicator during analysis
- **Error Handling**: Clear feedback for failed CVE lookups

## Installation

### Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for NVD API access)
- No server or dependencies required - runs entirely in the browser

### Setup

1. **Download the file**:
   ```bash
   # Clone or download the repository
   git clone <repository-url>
   cd CVE_Age_Tracker
   ```

2. **Open the application**:
   - Simply open `cve_age_tracker_carbon.html` in your web browser
   - Or double-click the file to launch it

3. **Alternative: Serve locally** (optional):
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Python 2
   python -m SimpleHTTPServer 8000
   
   # Then navigate to http://localhost:8000/cve_age_tracker_carbon.html
   ```

## Usage

### Basic Analysis

1. **Enter CVE IDs**:
   - Type or paste CVE IDs in the text area
   - Supports multiple formats:
     - One per line: `CVE-2024-1234`
     - Comma-separated: `CVE-2024-1234, CVE-2023-5678`
     - Mixed format with any separators

2. **Click "Analyze CVEs"**:
   - The application will fetch data from NVD
   - Progress indicator shows completion status
   - Results appear automatically when complete

3. **Review Results**:
   - **Summary Panel**: View overall statistics
   - **Timeline Chart**: Visualize CVE distribution over time
   - **Severity Sections**: Expand/collapse to view detailed CVE information
   - Click CVE IDs to view full details on NVD website

4. **Export Data**:
   - Click "📥 Download CSV" to export results
   - File includes all analyzed CVEs with complete metadata

### Understanding the Metrics

#### Age Categories
- **Recent**: < 90 days old (green)
- **Moderate**: 90-180 days old (yellow)
- **Old**: 180-365 days old (red)
- **Very Old**: > 365 days old (red)

#### Severity Levels
- **Critical**: CVSS 9.0-10.0 (red background)
- **High**: CVSS 7.0-8.9 (orange background)
- **Medium**: CVSS 4.0-6.9 (blue background)
- **Low**: CVSS 0.1-3.9 (green background)
- **N/A**: No CVSS score available (gray background)

#### Percentage Old Calculation
```
Percentage Old = (CVEs older than 6 months / Total successful CVEs) × 100
```
- Excludes errored CVEs from calculation
- Helps identify vulnerability debt in your systems

### Timeline Features

- **Toggle Views**: Switch between monthly and quarterly groupings
- **Interactive Bars**: Hover to see detailed breakdown
- **Click to Filter**: Click a bar segment to jump to that severity section
- **Color Legend**: Identifies severity levels at a glance

## API Information

### NVD API
- **Endpoint**: `https://services.nvd.nist.gov/rest/json/cves/2.0`
- **Rate Limits**: Public API (no key required)
  - 5 requests per 30 seconds
  - 50 requests per 30 seconds with API key
- **Documentation**: [NVD API Documentation](https://nvd.nist.gov/developers/vulnerabilities)

### Data Sources
- CVE descriptions from NVD
- CVSS v3.1, v3.0, and v2.0 scores
- Publication dates
- Last modified dates

## Technical Details

### Architecture
- **Single-page application**: No backend required
- **Client-side processing**: All analysis happens in the browser
- **Vanilla JavaScript**: No frameworks or build tools needed
- **IBM Carbon Design System**: Professional UI/UX standards

### Browser Compatibility
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### Performance
- Handles 100+ CVEs efficiently
- Parallel API requests for faster processing
- Responsive UI during data fetching
- Optimized rendering for large datasets

## Troubleshooting

### Common Issues

**CVEs not found**:
- Verify CVE ID format (CVE-YYYY-NNNNN)
- Check if CVE exists in NVD database
- Some very recent CVEs may not be available yet

**Slow loading**:
- NVD API rate limits may cause delays
- Large batches (50+) take longer to process
- Check your internet connection

**API errors**:
- NVD API may be temporarily unavailable
- Wait a few minutes and try again
- Check NVD status page for outages

**Display issues**:
- Clear browser cache
- Try a different browser
- Ensure JavaScript is enabled

## Version History

### Version 1.April_02_26 (Current)
- IBM Carbon Design System implementation
- Blue gradient header and buttons
- Colored summary panels
- Enhanced visual hierarchy
- "Built with Bob" branding
- Improved responsive design
- Subtle shading and shadows

### Previous Versions
- Original implementation with basic styling
- Timeline visualization added
- CSV export functionality
- Collapsible severity sections

## Contributing

Contributions are welcome! Please ensure:
- Code follows existing style patterns
- IBM Carbon Design principles are maintained
- All functionality remains intact
- Documentation is updated

## License

[Specify your license here]

## Support

For issues, questions, or suggestions:
- Open an issue in the repository
- Contact the development team
- Check NVD API documentation for API-related questions

## Acknowledgments

- **NVD**: National Vulnerability Database for CVE data
- **IBM Carbon Design System**: UI/UX design principles
- **Built with Bob**: Development assistance

---

**Note**: This application requires internet access to fetch CVE data from the National Vulnerability Database. No personal data is collected or stored.