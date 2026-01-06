# Thermodynamics Property Lookup Web App

A fast, interactive web application for looking up thermodynamic properties with automatic interpolation and unit conversion support.

## Features

- **Multi-material support**: Water, R-134a, Ideal Gases, and more
- **Automatic interpolation**: Linear interpolation between table values
- **Dual unit systems**: Metric (SI) and English (IP) units with automatic conversion
- **Extrapolation warnings**: Alerts when input values are outside table ranges
- **Beautiful UI**: Modern, responsive design with Tailwind CSS
- **Client-side only**: No backend required, runs entirely in the browser

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

## Setup Instructions

### 1. Add Your CSV Files

Place your CSV files in the `Tables/` directory organized by material:

```
Tables/
├── Water/
│   ├── saturated_water_T.csv
│   ├── saturated_water_P.csv
│   ├── superheated_water.csv
│   └── compressed_water.csv
├── R-134a/
│   ├── saturated_r134a_T.csv
│   └── saturated_r134a_P.csv
└── Ideal Gases/
    ├── air.csv
    ├── nitrogen.csv
    └── oxygen.csv
```

**CSV Format Requirements:**
- First row must contain column headers
- Use lowercase property names with units (e.g., `temperature°c`, `pressurempa`)
- Numeric data should be properly formatted
- Example format:

```csv
temperature°c,pressurempa,vfm3/kg,vgm3/kg,ufkj/kg,ugkj/kg,hfkj/kg,hgkj/kg,sfkj/kg·k,sgkj/kg·k
0.01,0.0006117,0.001000,206.00,0.00,2374.9,0.01,2500.9,0.0000,9.1555
20,0.0023392,0.001002,57.762,83.91,2402.3,83.91,2537.4,0.2965,8.6661
40,0.0073849,0.001008,19.515,167.53,2429.0,167.53,2573.5,0.5724,8.2558
```

### 2. Start a Local Server

The app requires a local web server to work properly (due to browser security restrictions with file uploads).

**Option A: Using Python 3**
```bash
cd thermo-lookup-app
python3 -m http.server 8000
```

**Option B: Using Python 2**
```bash
cd thermo-lookup-app
python -m SimpleHTTPServer 8000
```

**Option C: Using Node.js (npx)**
```bash
cd thermo-lookup-app
npx http-server -p 8000
```

**Option D: Using PHP**
```bash
cd thermo-lookup-app
php -S localhost:8000
```

### 3. Open in Browser

Navigate to:
```
http://localhost:8000
```

## How to Use

1. **Upload Tables**
   - Click "Upload Folder" to select your entire `Tables/` directory
   - Or click "Upload Individual Files" to select specific CSV files
   - Try "Demo Mode" to test with sample water data

2. **Select Unit System**
   - Choose between Metric (SI) or English (IP) units
   - All inputs and outputs will use the selected system

3. **Select Material**
   - Choose from available materials (Water, R-134a, etc.)

4. **Select Table**
   - Choose the specific property table (e.g., saturated by temperature, saturated by pressure)

5. **Perform Lookup**
   - Select your known property (X) from the dropdown
   - Enter its value
   - Select the property you want to find (Y)
   - Click "Calculate"

6. **View Results**
   - See all related properties (e.g., selecting "h" returns h_f, h_g, h_fg)
   - Check for extrapolation warnings if your value is outside the table range

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

**Files not loading:**
- Make sure you're using a local web server (not opening index.html directly)
- Check that CSV files are properly formatted with headers

**Properties not found:**
- Verify column names in CSV match expected patterns
- Check for typos or special characters

**Interpolation errors:**
- Ensure table data is sorted by the independent variable
- Verify numeric values are valid (no text in data rows)

**Demo mode not working:**
- Clear browser cache and reload
- Check browser console for JavaScript errors

## Technologies Used

- HTML5
- JavaScript (ES6+)
- [Tailwind CSS](https://tailwindcss.com/) - Styling
- [PapaParse](https://www.papaparse.com/) - CSV parsing

## License

Free to use for educational and personal purposes.
