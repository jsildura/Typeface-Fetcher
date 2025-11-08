# Typeface Fetcher

A powerful Chrome extension to download fonts from Adobe Fonts with optional Python integration for system-installable fonts. Features a beautiful Material Design 3 interface for easy font management.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Chrome](https://img.shields.io/badge/chrome-v88+-orange)
![Python](https://img.shields.io/badge/python-3.7+-green)

## Quick Start

1. **Install Extension** - Load unpacked in Chrome Developer Mode
2. **Visit Adobe Fonts** - Go to fonts.adobe.com
3. **Download** - Click extension icon and download fonts
4. **Optional: Python Integration** - Install [Native Host](https://github.com/jsildura/AdobeFontsNativeHost) for system-installable fonts

## Screenshots

> Screenshots coming soon

**Main Popup Interface**
- Clean Material Design 3 UI
- Real-time download progress
- Quick access to settings

**Settings Page**
- Comprehensive configuration options
- Advanced features toggle
- Python integration status

**Download in Action**
- ZIP creation
- Organized folder structure
- System notifications

## Features

### Core Features
- **One-Click Downloads** - Download fonts directly from Adobe Fonts pages
- **Collection Support** - Download entire font collections at once
- **Material Design 3** - Beautiful, modern UI following Google's latest design guidelines
- **Automatic Metadata** - Modifies font family names and styles for better organization
- **Real-time Progress** - Visual progress indicators for all downloads
- **Customizable Settings** - Configure download behavior to your preferences
- **Auto-organization** - Fonts automatically organized by family name

### Standard Mode (Default)
- **Concurrent Downloads** - Download multiple fonts simultaneously (configurable 1-10)
- **ZIP Creation** - Automatically package fonts into ZIP archives
- **Smart Detection** - Automatically detects font and collection pages
- **Responsive Design** - Works seamlessly at any window size
- **Web-Only Fonts** - Fonts work in web applications but may not install system-wide

### Advanced Mode (Optional Python Integration)
- **System-Installable Fonts** - Fonts can be installed directly into Windows Font Library
- **fontTools Processing** - Repairs font metadata for full system compatibility
- **Native Messaging** - Communicates with local Python host for font processing
- **One-Time Setup** - Simple installer configures everything automatically
- **Automatic Detection** - Extension detects if Python integration is available

## Comparison: Standard vs Advanced Mode

| Feature | Standard Mode | Advanced Mode (Python) |
|---------|--------------|------------------------|
| **Download Fonts** | Yes | Yes |
| **ZIP Creation** | Yes | Yes |
| **Web Applications** | Works | Works |
| **System Installation** | May fail | Always works |
| **Font Library** | Limited | Full compatibility |
| **Setup Required** | None | One-time (installer) |
| **Python Needed** | No | Yes (3.7+) |
| **Processing Speed** | Fast | Slightly slower |
| **Recommended For** | Web designers | System-wide font users |

## Installation

### Extension Setup

#### Loading the Extension

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer mode** (toggle in top-right corner)
3. Click **Load unpacked**
4. Select the `chrome-extension` folder
5. The extension icon should appear in your toolbar

### Python Integration Setup (Optional)

For system-installable fonts, install the Native Host:

#### Requirements
- Python 3.7 or higher installed on your system
- Windows operating system (Linux/Mac support coming soon)

#### Installation Steps

1. **Download the Native Host Installer**
   - Get the latest release from: [Adobe Fonts Native Host](https://github.com/jsildura/AdobeFontsNativeHost/releases)
   - File: `AdobeFontsNativeHost-Setup.exe`

2. **Run the Installer**
   - Double-click the downloaded file
   - Choose installation directory (default: `%LOCALAPPDATA%\AdobeFontsExtension`)
   - Wait for Python environment setup (1-2 minutes)
   - The installer may show "Not Responding" - this is normal during Python setup

3. **Configure Extension ID**
   - After installation, a dialog will appear with setup instructions
   - Go to `chrome://extensions/`
   - Enable Developer mode and find your Extension ID
   - Edit: `%LOCALAPPDATA%\AdobeFontsExtension\com.adobefonts.processor.json`
   - Replace `EXTENSION_ID_PLACEHOLDER` with your actual ID

4. **Enable in Extension**
   - Open extension options
   - Navigate to "Advanced Features" section
   - Toggle on "Python Integration"
   - If the toggle won't enable, the native host is not properly configured

5. **Verify Installation**
   - The extension will check for the native host
   - If successful, you'll see "Python Integration enabled"
   - Downloaded fonts will now be system-installable

## Usage Guide

### Downloading a Font Family

1. Navigate to any font page on [fonts.adobe.com](https://fonts.adobe.com)
   - Example: `https://fonts.adobe.com/fonts/proxima-nova`

2. Click the extension icon in your toolbar

3. The popup will show:
   - Font family name
   - Number of variations
   - Download options

4. Click **Download Fonts** button

5. Fonts will be downloaded to:
   ```
   Downloads/adobe-fonts/[Font Family Name]/
   ```

### Downloading a Collection

1. Navigate to a collection page
   - Example: `https://fonts.adobe.com/collections/fonts-for-the-bauhaus-look`

2. Click the extension icon

3. Review collection details:
   - Collection name
   - Number of fonts

4. Click **Download Collection**

5. Each font family will be downloaded separately

### Using Settings

Click the **Settings** icon in the popup or right-click the extension icon → Options

#### Available Settings

| Setting | Description | Default |
|---------|-------------|---------|
| **Create ZIP** | Package fonts into ZIP archives | On |
| **Modify Metadata** | Update font family names and styles | On |
| **Concurrent Downloads** | Number of simultaneous downloads (1-10) | 5 |
| **Auto-organize** | Organize fonts into family folders | On |
| **Show Notifications** | Display download completion notifications | On |
| **Debug Mode** | Enable detailed console logging | Off |
| **Python Integration** | Enable system-installable font processing | Off |

## UI Features

### Material Design 3
- **Dynamic Color System** - Adaptive color palette
- **Elevated Cards** - Subtle shadows and depth
- **Smooth Animations** - Polished transitions
- **Typography Scale** - Consistent text hierarchy
- **Interactive States** - Hover, focus, and press feedback

### Responsive Layout
- Optimized for popup (400px width)
- Settings page adapts to any screen size
- Touch-friendly controls
- Keyboard navigation support

## Project Structure

```
chrome-extension/
├── manifest.json                 # Extension configuration (MV3)
├── background.js                 # Service worker
├── content.js                    # Page scraping logic
│
├── popup/
│   ├── popup.html               # Main popup interface
│   ├── popup.css                # Popup-specific styles
│   └── popup.js                 # Popup controller
│
├── options/
│   ├── options.html             # Settings page
│   ├── options.css              # Settings styles
│   └── options.js               # Settings controller
│
├── styles/
│   └── material3.css            # Material Design 3 system
│
├── icons/
│   ├── icon16.png               # Toolbar icon (small)
│   ├── icon48.png               # Extension management
│   ├── icon128.png              # Chrome Web Store
│   ├── icon.svg                 # Source icon
│   └── create-placeholder-icons.html
│
├── lib/
│   ├── jszip.min.js            # ZIP creation (download required)
│   ├── opentype.min.js         # Font metadata (optional)
│   └── README.md
│
└── scripts/
    ├── download-libs.js         # Library downloader
    └── generate-icons.js        # Icon generator
```

## Technical Details

### Manifest V3 Compliance
- Uses Service Worker instead of background page
- No remote code execution
- Minimal permissions (activeTab, storage, downloads)
- Host permissions limited to fonts.adobe.com
- CSP compliant

### Browser Compatibility
- **Minimum Chrome Version**: 88+
- **Manifest Version**: 3
- **Architecture**: Modular, event-driven

### Performance
- **Concurrent Downloads**: Up to 10 simultaneous
- **Memory Efficient**: Streams large files
- **Non-blocking**: Doesn't freeze browser
- **Optimized**: Minimal resource usage

### Debugging

Enable **Debug Mode** in settings to see:
- Content script activity
- Background worker messages
- Download progress
- Error details

View logs:
- Press `F12` to open DevTools
- Go to Console tab
- Filter by "Adobe Fonts"

## Privacy & Security

- **No Data Collection** - Extension does not track or collect any user data
- **No Remote Servers** - All processing happens locally
- **Minimal Permissions** - Only requests necessary permissions
- **Open Source** - Code is fully transparent and auditable
- **No Ads** - Completely ad-free experience

## Troubleshooting

### Extension Won't Load
- Check Chrome version (requires 88+)
- Verify all icons are present
- Check manifest.json syntax
- Look for errors in chrome://extensions/

### Fonts Not Downloading
- Ensure you're on fonts.adobe.com
- Refresh the page
- Check Downloads folder permissions
- Enable Debug Mode for detailed logs

### ZIP Creation Fails
- Verify jszip.min.js is in lib/ folder
- Check browser console for errors
- Try disabling "Create ZIP" in settings

### Metadata Not Modified
- Ensure opentype.min.js is present (optional feature)
- Check if fonts are actually OTF/TTF format
- Disable feature in settings if causing issues

### Python Integration Won't Enable
- Verify Python 3.7+ is installed on your system
- Check that the native host installer completed successfully
- Ensure the Extension ID in `com.adobefonts.processor.json` matches your actual extension ID
- Verify the path in the JSON file has properly escaped backslashes (double backslashes)
- Try reinstalling the native host
- Check for errors in Chrome's native messaging logs

### Fonts Still Not System-Installable
- Confirm Python Integration is enabled in settings
- Check that fontTools was installed correctly (installer should have done this)
- Verify the batch file path is correct in the JSON manifest
- Test the Python host manually: Run `%LOCALAPPDATA%\AdobeFontsExtension\font_processor_wrapper.bat`
- Check Windows Event Viewer for Python errors

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## Credits

### Extension
- **Material Design 3** - by Google
- **JSZip** - by Stuart Knightley
- **opentype.js** - by Frederik De Bleser
- **Roboto Font** - by Google
- **Material Symbols** - by Google

### Python Integration (Optional)
- **fontTools** - by Just van Rossum and others
- **Python** - Python Software Foundation
- **NSIS** - Nullsoft Scriptable Install System

## Support

- **Issues**: [GitHub Issues](https://github.com/jsildura/adobe-fonts-downloader/issues)
- **Discussions**: [GitHub Discussions](https://github.com/jsildura/adobe-fonts-downloader/discussions)
- **Native Host Issues**: [Native Host Issues](https://github.com/jsildura/AdobeFontsNativeHost/issues)

## Roadmap

### Planned Features
- [ ] Chrome Web Store publication
- [ ] Collection batch download optimization
- [ ] Font preview before download
- [ ] Multiple font format support (WOFF, WOFF2)
- [ ] Download history
- [ ] Favorite fonts bookmarking
- [ ] Dark mode support
- [ ] Export settings

### Platform Expansion
- [ ] Firefox version
- [ ] macOS native host support
- [ ] Linux native host support

---

**Made with Material Design 3**

If you find this extension helpful, please consider starring the repository on GitHub.
