# Radar QPF Map Setup

This repo contains a standalone Leaflet viewer in `index.html`.

## Publish with GitHub Pages

1. Open this repo on GitHub.
2. Go to **Settings**.
3. Go to **Pages**.
4. Under **Build and deployment**, choose:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
5. Save.

Expected URL:

`https://mefferso.github.io/Radar-QPF-map/`

## Current map features

- Leaflet map centered over southeast Louisiana / south Mississippi / south Alabama
- KHDC radar toggle
- KMOB radar toggle
- MRMS toggle
- Accumulation-period dropdown
- Opacity slider
- Base map selector
- Radar site markers
- Approximate 124 nm radar range rings
- Approximate precip legend

## Important note

The map shell is built and functional, but KHDC/KMOB storm-total precip layer names may need refinement depending on the exact public NOAA/RadarServer service that exposes those products.

The layer config is in `index.html`:

```js
const precipLayerConfig = {
  khdc: {
    label: "KHDC Storm Total Precip",
    url: "https://opengeo.ncep.noaa.gov/geoserver/conus/conus_bref_qcd/ows",
    layers: "conus_bref_qcd"
  },
  kmob: {
    label: "KMOB Storm Total Precip",
    url: "https://opengeo.ncep.noaa.gov/geoserver/conus/conus_bref_qcd/ows",
    layers: "conus_bref_qcd"
  },
  mrms: {
    label: "MRMS QPE / Precip Accumulation",
    url: "https://opengeo.ncep.noaa.gov/geoserver/mrms/ows",
    layers: "mrms:MultiSensor_QPE_01H_Pass2"
  }
};
```

## MRMS layer period examples

The accumulation dropdown currently maps to these example layer names:

- `mrms:MultiSensor_QPE_01H_Pass2`
- `mrms:MultiSensor_QPE_03H_Pass2`
- `mrms:MultiSensor_QPE_06H_Pass2`
- `mrms:MultiSensor_QPE_24H_Pass2`

## Good next upgrades

- Confirm exact WMS endpoint/layer names for KHDC and KMOB storm-total precipitation
- Add valid time / timestamp display
- Add click-to-query precip value under cursor
- Add CWA/county/parish overlays
- Add looping frames if time-enabled layers are available
