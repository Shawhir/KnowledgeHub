# GLTF Manifesto

This repository contains the markdown version of the GLTF Manifesto maintained by the Creative Team at Esri R&D Zurich.

## Structure

- `/docs/GLTF_Manifesto.md` – main document
- `/docs/images/` – visual examples referenced in the markdown

This is based on the 2022.0 version and will serve as the foundation for future static documentation or PDF export.

## Development

To work locally, you need python installed on your system. After a `git clone`, run

```bash
pip install -r requirements.txt
```

to install mkdocs. You can now start the dev server by using

```bash
mkdocs serve
```

## Deployment

Every push to `main` is automatically built and deployed to qawebgis with [WebGIS/actions-publish-pages](https://devtopia.esri.com/WebGIS/actions-publish-pages). For details see [`.github/workflows/docs-deploy.yml`](.github/workflows/docs-deploy.yml).
