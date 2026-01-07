# Thermodynamics Property Lookup Web App

A fast, interactive web application for looking up thermodynamic properties with automatic interpolation and unit conversion support.

**✨ NEW: All data is now embedded! Just download and open `index.html` - no setup required!**

## Features

- **Self-contained**: All 18 thermodynamic tables embedded directly in the HTML file
- **Zero setup**: Download and double-click to run - no installation, no uploads, no server needed
- **Multi-material support**: Water, R-134a, Ideal Gases pre-loaded
- **Automatic interpolation**: Linear interpolation between table values
- **Dual unit systems**: Metric (SI) and English (IP) units with automatic conversion
- **Extrapolation warnings**: Alerts when input values are outside table ranges
- **Beautiful UI**: Modern, responsive design with Tailwind CSS
- **Works offline**: Runs entirely in the browser with no internet required

## Project Structure

```
thermo-lookup-app/
├── index.html          # Main application file
├── Tables/             # CSV data files directory
│   ├── Water/          # Water property tables
│   ├── R-134a/         # R-134a refrigerant tables
│   └── Ideal Gases/    # Ideal gas property tables
└── README.md           # This file
```

## Quick Start (No Setup Required!)

### Step 1: Download
Download `index.html` from this repository (or clone the repo)

### Step 2: Open
Double-click `index.html` to open it in your web browser

### Step 3: Use
1. Select your material (Water, R-134a, or Ideal Gases)
2. Choose a property table
3. Enter your known property value
4. Get interpolated results instantly!

**That's it!** All thermodynamic data is embedded - no uploads, no server, no configuration needed.

## Pre-loaded Data

The app includes 18 complete thermodynamic property tables:

**Water (5 tables):**
- A-4 T Saturated Water
- A-5 P Saturated Water
- A-6 Superheated Water
- A-7 Compressed Water
- A-8 Saturated Ice-Water Vapor

**R-134a (3 tables):**
- A-11 T Saturated R-134a
- A-12 P Saturated R-134a
- A-13 Superheated R-134a

**Ideal Gases (10 tables):**
- Air, Nitrogen, Oxygen, Carbon Dioxide, Carbon Monoxide
- Hydrogen, Water Vapor, Monoatomic Oxygen, Hydroxyl
- Atmosphere at High Altitude

## How to Use

The app opens ready to use with all data pre-loaded!

1. **Select Unit System**
   - Choose between Metric (SI) or English (IP) units
   - All inputs and outputs will use the selected system

2. **Select Material**
   - Choose from Water, R-134a, or Ideal Gases

3. **Select Table**
   - Choose the specific property table (e.g., saturated by temperature, saturated by pressure)

4. **Perform Lookup**
   - Select your known property (X) from the dropdown
   - Enter its value
   - Select the property you want to find (Y)
   - Click "Calculate"

5. **View Results**
   - See all related properties (e.g., selecting "h" returns h_f, h_g, h_fg)
   - Check for extrapolation warnings if your value is outside the table range

**Optional:** Upload custom CSV files using the "Upload Different Files" link if you need additional tables

## Unit Conversions

The app automatically handles conversions between:

| Property | Metric (SI) | English (IP) |
|----------|-------------|--------------|
| Temperature | °C | °F |
| Pressure | MPa | psi |
| Specific Volume (v) | m³/kg | ft³/lb |
| Internal Energy (u) | kJ/kg | BTU/lb |
| Enthalpy (h) | kJ/kg | BTU/lb |
| Entropy (s) | kJ/(kg·K) | BTU/(lb·°R) |

## Supported Property Naming

The app recognizes these property patterns:
- `temperature`, `temp`, `T`
- `pressure`, `P`
- `v`, `vf`, `vg`, `vfg` (specific volume)
- `u`, `uf`, `ug`, `ufg` (internal energy)
- `h`, `hf`, `hg`, `hfg` (enthalpy)
- `s`, `sf`, `sg`, `sfg` (entropy)

## Interpolation Method

The app uses linear interpolation:
```
y = y1 + (y2 - y1) * (x - x1) / (x2 - x1)
```

Where:
- `x` is your input value
- `x1, x2` are the table values bracketing your input
- `y1, y2` are the corresponding property values
- `y` is the interpolated result

## Troubleshooting

**App not opening:**
- Make sure you're opening `index.html` in a modern web browser (Chrome, Firefox, Safari, Edge)
- File size is ~325KB - download may take a moment

**Data not showing:**
- All data is embedded - no uploads needed
- If you see "Upload" screen, click "Try Demo Mode" or refresh the page
- Clear browser cache if you have an old version

**Properties not found:**
- Make sure you select a property that exists in your chosen table
- Check table column headers to see available properties

**Interpolation errors:**
- Verify your input value is within the table range (or close to it)
- Extrapolation warnings are normal for values outside the table

**Wrong results:**
- Double-check you're using the correct unit system (Metric vs English)
- Verify you selected the correct table and material

## Technologies Used

- HTML5
- JavaScript (ES6+)
- [Tailwind CSS](https://tailwindcss.com/) - Styling
- [PapaParse](https://www.papaparse.com/) - CSV parsing

## License

Free to use for educational and personal purposes.
