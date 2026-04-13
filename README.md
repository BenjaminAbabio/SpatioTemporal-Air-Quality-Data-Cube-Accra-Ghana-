## Data Sources & Variables
The cube integrates the following parameters at a synchronized 1km spatial resolution:
- **Ground Truth:** PM2.5 concentrations (Low-cost sensor network).
- **Aerosols:** Aerosol Optical Depth (AOD) at 550nm (MODIS/Sentinel-5P).
- **Meteorology:** 2m Temperature and Relative Humidity (ERA5-Land).
- **Dynamics:** Planetary Boundary Layer Height (PBLH) (ERA5).
- **Hydrology:** Daily Precipitation (CHIRPS/GPM).

## Technical Implementation
The project utilizes Python and Google Earth Engine to perform:
1. **SpatioTemporal Matching:** Aligning asynchronous satellite overpasses with hourly ground station readings.
2. **Feature Engineering:** Calculation of Julian days, hour of day, and coordinate encoding.
3. **Data Imputation:** Filling ground-station gaps using Random Forest regressor logic.
4. **Coordinate Harmonization:** Projecting all data to a common CRS (EPSG:32630) for spatial consistency.

## Data Structure
The final output is a flattened GeoDataFrame/CSV containing `[timestamp, location_id, latitude, longitude, pm25, aod, temp, rh, pbl, precip]`.

## Requirements
- Python 3.8+
- Geopandas
- Scikit-learn
- Scipy (cKDTree for nearest-neighbor matching)
