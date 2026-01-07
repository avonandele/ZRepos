# Using Your Thermodynamic Property Tables

## Your Data Files

You now have **18 thermodynamic property tables** loaded:

### Water (5 tables)
- A-4 T Saturated Water - 77 rows
- A-5 P Saturated Water - 74 rows
- A-6 Superheated Water - 549 rows
- A-7 Compressed Water - 112 rows
- A-8 Saturated Ice-Water Vapor - 23 rows

### R-134a (3 tables)
- A-11 T Saturated R-134a - 57 rows (temperature-based)
- A-12 P Saturated R-134a - 35 rows (pressure-based)
- A-13 Superheated R-134a - 262 rows

### Ideal Gases (10 tables)
- A-16 Atmosphere at High Altitude - 44 rows
- A-17 Air - 122 rows
- A-18 Nitrogen - 157 rows
- A-19 Oxygen - 157 rows
- A-20 Carbon Dioxide - 157 rows
- A-21 Carbon Monoxide - 157 rows
- A-22 Hydrogen - 81 rows
- A-23 Water Vapor - 157 rows
- A-24 Monoatomic Oxygen - 37 rows
- A-25 Hydroxyl - 37 rows

## How to Use the App

### Option 1: Download and Use Locally (Recommended)

1. **Download from GitHub:**
   - Go to: https://github.com/avonandele/ZRepos
   - Switch to branch: `claude/setup-thermo-lookup-app-IGbq1`
   - Click "Code" → "Download ZIP"
   - Extract the ZIP file

2. **Open the App:**
   - Navigate to: `thermo-lookup-app/`
   - Double-click `index.html` to open in your browser

3. **Upload Your Tables:**
   - Click "Upload Folder"
   - Select the `Tables/` folder
   - All your CSV files will load automatically!

### Option 2: Use GitHub Pages (If you enable it)

Enable GitHub Pages for your repo to use it online without downloading.

## Example Lookup - Saturated Water

Let's try finding properties of saturated water at 50°C:

1. **Select Material:** Water
2. **Select Table:** A-4 T Saturated Water.csv
3. **Choose Unit System:** Metric (SI) or English (IP)
4. **Known Property (X):** T (°C)
5. **Value:** 50
6. **Find Property (Y):** Enthalpy (h)
7. **Click Calculate**

You'll get:
- hf (saturated liquid enthalpy)
- hfg (enthalpy of vaporization)
- hg (saturated vapor enthalpy)

## Example Lookup - Ideal Gas (Air)

Finding air properties at 300 K:

1. **Select Material:** Ideal Gases
2. **Select Table:** A-17 Air.csv
3. **Known Property (X):** T (K)
4. **Value:** 300
5. **Find Property (Y):** Enthalpy (h)
6. **Click Calculate**

Result: Interpolated enthalpy value at exactly 300 K

## Properties Available

The app recognizes these property types:
- **T** - Temperature
- **P, Psat** - Pressure (saturated pressure)
- **v, vf, vg, vfg** - Specific volume (liquid, gas, difference)
- **u, uf, ug, ufg** - Internal energy
- **h, hf, hg, hfg** - Enthalpy
- **s, sf, sg, sfg** - Entropy
- **P_r, v_r** - Relative pressure/volume (ideal gases)
- **s°** - Standard entropy

## Unit Conversions

Switch between Metric and English units anytime:

**Metric (SI):**
- Temperature: °C or K
- Pressure: kPa or MPa
- Energy: kJ/kg
- Entropy: kJ/(kg·K)

**English (IP):**
- Temperature: °F
- Pressure: psi
- Energy: BTU/lb
- Entropy: BTU/(lb·°R)

The app automatically converts your input and output!

## Tips

1. **Extrapolation Warning:** If your input value is outside the table range, you'll see a yellow warning
2. **Related Properties:** Selecting "h" finds all enthalpy values (hf, hg, hfg)
3. **Interpolation:** The app uses linear interpolation between table values
4. **Multiple Lookups:** Click "New Lookup" to start over or "Back to Input" to change values

## Example Lookup - R-134a Refrigerant

Finding R-134a properties at -30°C:

1. **Select Material:** R-134a
2. **Select Table:** A-11 T Saturated R-134a.csv
3. **Known Property (X):** T (°C)
4. **Value:** -30
5. **Find Property (Y):** Enthalpy (h)
6. **Click Calculate**

Result: Interpolated hf, hfg, hg values at -30°C

Or if you know pressure instead:
1. **Select Table:** A-12 P Saturated R-134a.csv
2. **Known Property (X):** P (kPa)
3. **Value:** 100
4. **Find Property (Y):** Temperature (T) or any other property

## Troubleshooting

**Property not found?**
- Make sure you select a property that exists in your chosen table
- Check the CSV file headers to see available properties

**Wrong results?**
- Verify you're using the correct unit system
- Check that your input value is within the table range
- Ensure CSV data is properly formatted with numeric values

Enjoy your thermodynamic property lookup app!
