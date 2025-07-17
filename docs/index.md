# Welcome to **FEZrs**

**FEZrs** is a modern, modular, and open-source Python library by [**FEZtool**](https://feztool.com/), designed for **remote sensing** and **geospatial analysis**.

From loading satellite images to extracting advanced features and running machine learning pipelines — FEZrs has your back.

Whether you're a researcher, student, or GIS developer, you can quickly plug FEZrs into your workflows for fast, scalable, and reproducible results.

---

## What You Can Do with FEZrs

- Load and process **GeoTIFF (.tif)** satellite imagery
- Apply **machine learning** and **deep learning** tools for land classification
- Extract **spectral**, **textural**, and **spatial** features (e.g., NDVI, GLCM)
- Chain tools into custom pipelines with the `BaseTool` architecture
- Perform **batch processing** for large-scale image datasets
- Run everything with **minimal dependencies** — even without GDAL

---

## Project Goals

- 🧩 **Modular design**: Build your own tools or extend existing ones with ease
- 🧪 **Scientific utility**: Help researchers build reproducible and trustable pipelines
- 🛠 **Lightweight processing**: Reduce dependency on heavy tools like GDAL
- 🎓 **Education-first**: Empower learners and professionals with open, readable code
- 🌐 **Community-focused**: Enable collaboration in the geospatial and EO community

---

## Who’s It For?

- Remote sensing researchers & Earth observation scientists
- GIS developers & spatial data analysts
- Students & educators in geospatial fields
- Data scientists exploring satellite data
- Anyone curious about the **Earth from above**

---

## Why Open Source?

FEZrs is free and open because we believe in:

- **Transparency**: You should trust the tools you use
- **Reproducibility**: Share results, not just code
- **Education**: Make advanced tools accessible to all
- **Community**: Join us in building the future of geospatial AI

---

## Installation

You can install **FEZrs** using your preferred Python package manager:

### Using `pip` (PyPI)

```bash
pip install fezrs
```

### Using `conda` (Anaconda)

```bash
conda install -c FEZtool fezrs
```

### Using `mamba` (optional, faster conda alternative)

```bash
mamba install FEZtool::fezrs
```

> **Note:** The `mamba` command requires [Mamba](https://github.com/mamba-org/mamba) to be installed. If it's not installed, use the `conda` command instead.

## Usage

Example of applying a Gaussian filter to an image:

```python
from fezrs import EqualizeRGBCalculator

equalize = EqualizeRGBCalculator(
    blue_path="path/to/your/image_band.tif",
    green_path="path/to/your/image_band.tif",
    red_path="path/to/your/image_band.tif",
)

equalize.chart_export(output_path="./your/export/path")
equalize.execute(output_path="./your/export/path")
```

## **Modules**

FEZrs embraces the **"simple yet powerful"** design principle.

Most tools in this library share a **unified structure** and can be used in a similar way — this makes learning and using FEZrs extremely easy and intuitive.

> Unless noted otherwise, nearly **all modules can be used as shown in the [Usage](docs/getting-started.md) section**.

These modules serve as **core calculators** for the main tool categories like:

- `change_detection`
- `clustering`
- `filters`
- `glcm`
- `hsv`
- `image_enhancement`
- `import_tools`
- `mosaic`
- `pca`
- `spectral_indices`
- `spectral_profile`
- `svm`

Each module is accessible directly and can be plugged into custom workflows or pipelines built on `BaseTool`.

---

## Module Overview Table

| Module                    | Input Bands    | Parameters                          | Description                           | Tool Category     |
| ------------------------- | -------------- | ----------------------------------- | ------------------------------------- | ----------------- |
| KMeansCalculator          | 1–N            | `n_clusters`, `init`, `max_iter`    | Applies K-Means clustering            | Clustering        |
| GuassianCalculator        | 1              | `kernel_size`, `sigma`              | Gaussian blur filter                  | Filters           |
| LaplacianCalculator       | 1              | `ksize`                             | Edge detection via Laplacian operator | Filters           |
| MeanCalculator            | 1              | `kernel_size`                       | Mean (box) filter                     | Filters           |
| MedianCalculator          | 1              | `kernel_size`                       | Median noise reduction                | Filters           |
| SobelCalculator           | 1              | `dx`, `dy`, `ksize`                 | Sobel edge detector                   | Filters           |
| GLCMCalculator            | 1              | `distances`, `angles`, `properties` | Texture extraction (GLCM)             | GLCM              |
| HSVCalculator             | RGB            | —                                   | Converts RGB to HSV                   | HSV               |
| IRHSVCalculator           | IR, R, G       | —                                   | Alternative HSV calc with IR          | HSV               |
| AdaptiveCalculator        | 1              | `clip_limit`, `tile_grid_size`      | Adaptive histogram equalization       | Image Enhancement |
| AdaptiveRGBCalculator     | RGB            | same as above                       | Adaptive hist. for RGB images         | Image Enhancement |
| EqualizeCalculator        | 1              | —                                   | Global histogram equalization         | Image Enhancement |
| EqualizeRGBCalculator     | RGB            | —                                   | Equalization for RGB                  | Image Enhancement |
| FloatCalculator           | 1              | —                                   | Converts bands to float32             | Image Enhancement |
| GammaCalculator           | 1              | `gamma`                             | Gamma correction                      | Image Enhancement |
| GammaRGBCalculator        | RGB            | `gamma`                             | Gamma correction for RGB              | Image Enhancement |
| LogAdjustCalculator       | 1              | `gain`                              | Logarithmic brightness adjust         | Image Enhancement |
| OriginalCalculator        | 1              | —                                   | Returns unmodified input              | Image Enhancement |
| OriginalRGBCalculator     | RGB            | —                                   | Returns RGB input unchanged           | Image Enhancement |
| SigmoidAdjustCalculator   | 1              | `gain`, `cutoff`                    | Sigmoid contrast adjustment           | Image Enhancement |
| PCACalculator             | N              | `n_components`                      | Principal Component Analysis          | PCA               |
| AFVICalculator            | NIR, Red, Blue | —                                   | Calculates AFVI index                 | Spectral Indices  |
| BICalculator              | SWIR1, SWIR2   | —                                   | Brightness Index                      | Spectral Indices  |
| NDVICalculator            | NIR, Red       | —                                   | NDVI vegetation index                 | Spectral Indices  |
| NDWICalculator            | Green, NIR     | —                                   | NDWI water index                      | Spectral Indices  |
| SAVICalculator            | NIR, Red       | `L`                                 | Soil Adjusted Vegetation Index        | Spectral Indices  |
| UICalculator              | Blue, Red      | —                                   | Urban Index                           | Spectral Indices  |
| SpectralProfileCalculator | N              | `pixels`, `wavelengths`             | Extracts spectral signature           | Spectral Profile  |

---

## License

Released under the [MIT License](https://github.com/FEZtool-team/FEZrs/blob/main/LICENSE).
Use it freely in academic, commercial, or personal projects — just give us a shout-out!

---

## Stay in Touch

- 🌐 Website: [feztool.com](https://feztool.com/)
- 📧 Email: [info@feztool.com](mailto:info@feztool.com)
- 🧪 Explore more: [FEZtool GitHub](https://github.com/FEZtool-team)
