# ThaparVerse

Interactive 3D campus portal for students of Thapar Institute of Engineering and Technology (TIET), Patiala. Explore campus buildings in 3D, hover to see building details, and (planned) ask an AI chatbot about professors, classes and campus facilities.

> **Status:** work in progress. See the roadmap below for what is done and what is planned.

## Features

- 3D campus scene built in Blender and exported as glTF/GLB
- Orbit, pan and zoom navigation (Three.js)
- Hover detection on buildings with an info tooltip (CSED, Library, LP Block)
- Building details stored in JSON (`public/data/buildings.json`), editable without touching code
- AI chatbot for professor, class and facility queries *(planned)*
- AWS deployment: S3 + CloudFront with GitHub Actions CI/CD *(planned)*

## Tech stack

| Area | Tools |
|------|-------|
| 3D modeling | Blender, GIS/OSM + satellite reference |
| Web 3D | Three.js, GLTFLoader, DRACOLoader, OrbitControls |
| Frontend | HTML, CSS, JavaScript |
| Cloud / DevOps | AWS S3, CloudFront, GitHub Actions |

## Project structure

```
thaparverse/
├── public/
│   ├── index.html            # 3D viewer + hover tooltip
│   ├── data/buildings.json   # building metadata
│   └── models/               # exported .glb files (campus.glb)
├── blender/                  # .blend source files (optional, large)
├── docs/                     # screenshots, notes
└── .github/workflows/        # CI/CD
```

## Run locally

```bash
git clone https://github.com/<your-username>/thaparverse.git
cd thaparverse/public
python3 -m http.server 8000
```

Open http://localhost:8000. Place your exported model at `public/models/campus.glb`.

## Blender export rules

Object names in Blender must match the keys in `public/data/buildings.json`:

- `CSED_Building`
- `Library_Building`
- `LP_Building`

Export with **File > Export > glTF 2.0 (.glb)** and enable **Draco mesh compression**.

## Roadmap

- [x] Campus layout from GIS/satellite data
- [ ] Model CSED, Library, LP Block
- [ ] Export optimized GLB
- [ ] Hover info tooltips
- [ ] Add more buildings
- [ ] AI chatbot (professors, classes, facilities)
- [ ] Deploy to AWS (S3 + CloudFront)
- [ ] CI/CD with GitHub Actions

## Screenshots

Add screenshots to `docs/` and link them here.

## License

MIT
