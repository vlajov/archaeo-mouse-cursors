# Themed Archaeological Cursors

A collection of themed cursor files designed with an archaeological aesthetic for Windows OS

## Contents

- `Busy.ani` - Animated cursor for busy/loading states
- `Handwriting.cur` - Cursor for handwriting/pen input
- `Help Select.cur` - Cursor for help selection
- `Link Select.cur` - Cursor for hyperlink selection
- `Normal Select.cur` - Standard selection cursor
- `Text Select.cur` - Cursor for text selection
- `Working in Background.ani` - Animated cursor for background processes

## Personal Installation

### Method 1: Control Panel (Recommended)

1. **Download** all cursor files to a folder (e.g., `C:\Windows\Cursors\Archaeological`)
2. **Open Control Panel** → `Hardware and Sound` → `Mouse`
3. **Click** the `Pointers` tab
4. **Select** each cursor type and click `Browse`
5. **Navigate** to your cursor folder and select the appropriate file:
   - Normal Select → `Normal Select.cur`
   - Help Select → `Help Select.cur`
   - Working in Background → `Working in Background.ani`
   - Busy → `Busy.ani`
   - Text Select → `Text Select.cur`
   - Handwriting → `Handwriting.cur`
   - Link Select → `Link Select.cur`
6. **Click** `Apply` then `OK`

### Method 2: Registry Installation

1. **Download** cursors to `C:\Windows\Cursors\Archaeological\`
2. **Run** as Administrator: `regedit`
3. **Navigate** to `HKEY_CURRENT_USER\Control Panel\Cursors`
4. **Modify** these values:
   - `Arrow` → `C:\Windows\Cursors\Archaeological\Normal Select.cur`
   - `Help` → `C:\Windows\Cursors\Archaeological\Help Select.cur`
   - `AppStarting` → `C:\Windows\Cursors\Archaeological\Working in Background.ani`
   - `Wait` → `C:\Windows\Cursors\Archaeological\Busy.ani`
   - `IBeam` → `C:\Windows\Cursors\Archaeological\Text Select.cur`
   - `Crosshair` → `C:\Windows\Cursors\Archaeological\Handwriting.cur`
   - `Hand` → `C:\Windows\Cursors\Archaeological\Link Select.cur`
5. **Restart** or log off/on to apply changes

## Enterprise Deployment

For company-wide deployment using Active Directory Group Policy, see [GPO-DEPLOYMENT.md](GPO-DEPLOYMENT.md).

### Automated GPO Deployment Script

For automated GPO creation, use the PowerShell script: [Deploy-CursorGPO-Generic.ps1](Deploy-CursorGPO-Generic.ps1)

**Related Discussion**: [PS1 script to deploy custom mouse cursors works but files are not copied to client PCs](https://learn.microsoft.com/en-us/answers/questions/5610841/ps1-script-to-deploy-custom-mouse-cursors-works-bu)

## Compatibility

- **OS**: Windows 7, 8, 10, 11
- **Formats**: .cur (static), .ani (animated)
- **Architecture**: x86, x64

## License

Free for personal and commercial use.
