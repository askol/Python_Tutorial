# Python Tutorial — Local preview

To preview the documentation site locally you can use MkDocs with the Material theme.

Install (recommended inside a Python virtual environment):

```bash
python -m pip install --upgrade pip
pip install mkdocs mkdocs-material
```

Start a local dev server:

```bash
mkdocs serve
```

Open http://127.0.0.1:8000 in your browser to view the site. If `mkdocs` is not found, install the packages above or ensure your virtual environment is activated.

If you'd like, I can also add a small GitHub Actions workflow to build and deploy the site automatically.
