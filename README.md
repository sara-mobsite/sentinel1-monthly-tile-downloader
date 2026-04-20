# sentinel-monthly-tile-downloader

A Python workflow for downloading the best monthly **Sentinel-1** and **Sentinel-2** scenes for selected tiles from the **Microsoft Planetary Computer**.

This repository uses the **Sentinel-2 tiling grid**, which is based on the **Military Grid Reference System (MGRS)**. Tile IDs such as `21JXJ`, `24LTR`, or `21LXK` are used to define the area of interest for both Sentinel-1 and Sentinel-2 monthly downloads.

## Repository contents

This repo includes:

- **Sentinel-1 notebook** for monthly scene selection and download
- **Sentinel-2 notebook** for monthly best-scene selection using tile coverage and cloud filtering
- Export of clipped imagery, metadata, and summary tables

## Features

- Search **Sentinel-1** scenes from Microsoft Planetary Computer
- Search **Sentinel-2 L2A** scenes from Microsoft Planetary Computer
- Use **Sentinel-2 MGRS tiles** to define the area of interest
- Select the **best scene for each month** for each chosen tile
- Filter scenes by **minimum tile coverage**
- For Sentinel-1, download assets such as **VV** and **VH**
- For Sentinel-2, download selected bands and **SCL**

## Sentinel-1 workflow

The Sentinel-1 part of this repository is used to:

1. Search Sentinel-1 scenes for a selected tile and month
2. Evaluate scene coverage over the tile
3. Select the best monthly scene
4. Download the required SAR assets


## Sentinel-2 workflow

The Sentinel-2 notebook is designed to find the **best monthly Sentinel-2 scene** for a selected MGRS tile and save the clipped bands for that tile.

## Sentinel-2 bands saved

The Sentinel-2 workflow saves the following assets when available:

- `B01`
- `B02`
- `B03`
- `B04`
- `B05`
- `B06`
- `B07`
- `B08`
- `B8A`
- `B09`
- `B10`
- `B11`
- `B12`
- `SCL`

## Sentinel-2 quality criteria

The script uses the **Scene Classification Layer (SCL)** to estimate usable coverage.

### Clear / usable SCL classes
```python
CLEAR_SCL = np.array([4, 5, 6], dtype=np.int16)
