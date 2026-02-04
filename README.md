# Microsoft Print to PDF Printer Recovery

A step-by-step guide to restore the missing "Microsoft Print to PDF" printer on Windows 11 systems, particularly after updates or system changes.

## ⚠️ Important Prerequisites

- **Administrator privileges required** for all steps
- Ensure you have a backup of important system files before proceeding
- Recommended for Windows 11 24H2 Build 26100.4061 (post-update)

## 📁 Method 1: Using Driver from Working System (Recommended)

### Step 1: Obtain the Missing Driver Folder
From a functioning Windows 11 system (same or earlier build):

1. Navigate to: `C:\Windows\System32\DriverStore\FileRepository\`
2. Locate and copy the entire folder: `prnms009.inf_amd64_<hash>`
*(Replace `<hash>` with the specific hash value from the working system)*

### Step 2: Transfer and Install
1. Transfer the copied folder to the affected system
2. Navigate into the folder
3. **Right-click** on `prnms009.inf`
4. Select **"Install"**

## 📥 Method 2: Download Pre-packaged Driver

### Quick Download
Download the driver package from a Windows 11 24H2 Build 26100.4061 system:

**[prnms009.inf_amd64_5555b7fbfa8487e2.zip](https://github.com/IIPoliII/Microsoft-Print-to-PDF-Missing/prnms009.inf_amd64_5555b7fbfa8487e2.zip)**

### Installation Steps
1. **Download** the ZIP file
2. **Extract** contents to a temporary location (e.g., Desktop)
3. **Right-click** on `prnms009.inf`
4. Select **"Install"**

## 🔧 Complete Feature Reinstallation

After driver installation, perform a complete reinstall:

### Step 1: Uninstall Feature
1. Press `Windows + R`
2. Type `optionalfeatures` and press `Enter`
3. In **Windows Features** dialog:
- Uncheck **"Microsoft Print to PDF"**
- Click **OK** to uninstall

### Step 2: Stop Print Spooler
1. Press `Windows + R`
2. Type `services.msc` and press `Enter`
3. In **Services** window:
- Locate **"Print Spooler"**
- **Right-click** → Select **"Stop"**

### Step 3: Reinstall Feature
1. Press `Windows + R`
2. Type `optionalfeatures` and press `Enter`
3. In **Windows Features** dialog:
- Check **"Microsoft Print to PDF"**
- Click **OK** to reinstall

### Step 4: Restart Print Spooler
1. Return to **Services** window
2. Locate **"Print Spooler"**
3. **Right-click** → Select **"Start"**

## ✅ Verification

1. Open **Settings** → **Bluetooth & devices** → **Printers & scanners**
2. Verify **"Microsoft Print to PDF"** appears in printers list
3. Test by printing any document and selecting "Microsoft Print to PDF" as printer

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| "Install" option not available | Run Command Prompt as Admin → Navigate to folder → Run `pnputil /add-driver prnms009.inf` |
| Driver installation fails | Ensure Windows Update is current, then retry |
| Feature still missing | Restart system after completing all steps |

## 📝 Notes

- **System Compatibility**: This fix targets Windows 11 24H2 Build 26100.4061
- **Hash Variations**: Different Windows builds may have different hash values in folder names
- **Alternative Source**: If the provided driver doesn't work, obtain from a system with identical Windows build

## 🤝 Contributing

Found another working driver version? Submit a pull request or open an issue with:
- Windows version/build
- Driver folder hash
- Download link (if available)

---

**Disclaimer**: Use at your own risk. Always create system restore points before modifying system files.
