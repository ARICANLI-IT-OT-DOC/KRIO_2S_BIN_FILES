# KRIO Firmware Binaries

This directory contains pre-built firmware binaries for testing and deployment.

## Directory Structure

```
binaries/
├── KRIO-2S/         # KRIO-2S binaries
│   └── KRIO-2S.bin
├── KRIO-16DI/       # KRIO-16DI binaries
│   └── KRIO-16DI.bin
├── KRIO-8DO/        # KRIO-8DO binaries
│   └── KRIO-8DO.bin
├── KRIO-GNSS/       # KRIO-GNSS binaries
│   └── KRIO-GNSS.bin
└── README.md
```

## For Testers

### Quick Start

1. **Pull the latest code:**
   ```bash
   git pull
   ```

2. **Navigate to your model's directory:**
   ```bash
   cd binaries/KRIO-2S/      # For KRIO-2S model
   cd binaries/KRIO-16DI/    # For KRIO-16DI model
   cd binaries/KRIO-8DO/     # For KRIO-8DO model
   cd binaries/KRIO-GNSS/    # For KRIO-GNSS model
   ```

3. **Use the binary file:**
   - Each folder contains the latest binary for that model
   - Binary name matches the model name (e.g., `KRIO-2S.bin`)

4. **Flash to device** (via web interface or your preferred method)

## For Developers

### Building Binaries

After building the firmware, copy the binary to its model-specific folder:

```bash
# Build the firmware (make sure correct model is selected in menuconfig)
idf.py build

# Copy to appropriate model folder
cp build/KRIO-2S.bin binaries/KRIO-2S/      # For KRIO-2S
cp build/KRIO-16DI.bin binaries/KRIO-16DI/  # For KRIO-16DI
cp build/KRIO-8DO.bin binaries/KRIO-8DO/    # For KRIO-8DO
cp build/KRIO-GNSS.bin binaries/KRIO-GNSS/  # For KRIO-GNSS
```

### Important Notes

- **Only commit working binaries** - Test before pushing
- **Keep model binaries in their respective folders**
- **Update all model binaries together** when possible to keep versions in sync
- The binary name is automatically set based on your Kconfig model selection
- Binary files in `binaries/KRIO-*/` folders are tracked by git (exception to .gitignore)

## Binary Naming

The binary name is determined by the Kconfig model selection:
- `CONFIG_KRIO_2S` → `KRIO-2S.bin`
- `CONFIG_KRIO_16DI` → `KRIO-16DI.bin`
- `CONFIG_KRIO_8DO` → `KRIO-8DO.bin`
- `CONFIG_KRIO_GNSS` → `KRIO-GNSS.bin`

## Firmware Version

Check the firmware version in the binary by looking at `main/Kconfig`:
```
config KRIO_FIRMWARE_VERSION
    string "Firmware Version"
    default "V0.5"
```
