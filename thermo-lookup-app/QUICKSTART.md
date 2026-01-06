# Quick Start Guide

## The app is already running!

Your thermodynamic property lookup app is set up and ready to use.

### Access the App

Open your browser and navigate to:
```
http://localhost:8000
```

## Next Steps

### Option 1: Try Demo Mode (Recommended First)

1. Open http://localhost:8000
2. Click "Try Demo Mode (Sample Water Data)"
3. Select "Water" material
4. Select "saturated_water_T.csv" table
5. Choose unit system (Metric or English)
6. Try a lookup:
   - Known Property: `temperature°c`
   - Value: `50`
   - Find Property: `h`
   - Click "Calculate"

You should see interpolated values for h_f, h_g, and h_fg!

### Option 2: Upload Your Real Data

1. Copy all your CSV files to the `Tables/` directory following this structure:
   ```
   Tables/
   ├── Water/
   │   ├── your_water_table_1.csv
   │   └── your_water_table_2.csv
   ├── R-134a/
   │   └── your_r134a_tables.csv
   └── Ideal Gases/
       └── your_gas_tables.csv
   ```

2. Open http://localhost:8000
3. Click "Upload Folder" and select the `Tables/` directory
   - Or click "Upload Individual Files" to select specific CSV files

## CSV File Format

Your CSV files should look like this:

```csv
temperature°c,pressurempa,vfm3/kg,vgm3/kg,hfkj/kg,hgkj/kg
0.01,0.0006117,0.001000,206.00,0.01,2500.9
20,0.0023392,0.001002,57.762,83.91,2537.4
40,0.0073849,0.001008,19.515,167.53,2573.5
```

**Important:**
- First row = column headers (property names with units)
- Use lowercase for property names
- Include units in the header (e.g., `temperature°c`, `pressurempa`)

## Testing the Sample Data

A sample water table is already included at:
`Tables/Water/saturated_water_T.csv`

This contains saturated water properties from 0.01°C to 100°C.

## Stopping the Server

When you're done, stop the server with:
```bash
# Find the process
ps aux | grep "python3 -m http.server"

# Kill it (replace PID with actual process ID)
kill <PID>
```

Or simply close the terminal.

## Troubleshooting

**Can't access http://localhost:8000?**
- Check if the server is running: `curl http://localhost:8000`
- Make sure port 8000 isn't already in use
- Try a different port: `python3 -m http.server 8080`

**CSV files not uploading?**
- Make sure files have `.csv` extension
- Check that headers are on the first row
- Verify data is comma-separated

**Interpolation not working?**
- Ensure your known property value is within the table range
- Check that property names in CSV match what you're selecting
- Verify numeric data has no text characters

## Need Help?

Check the full README.md for:
- Detailed setup instructions
- Unit conversion reference
- Supported property naming conventions
- Interpolation methodology
