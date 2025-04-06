# 🔧 Basenji Setup Using `uv`

This repo adapts the original Basenji codebase for a fully `uv`-managed Python environment. It replicates the original `prespecified.yml` using `pip` and `pyproject.toml` for modern, portable dependency management.

---

## Setup

```bash
# Clone the fork
git clone https://github.com/calico/basenji.git
cd basenji

# Set up environment with Python 3.9
uv venv --python=3.9
uv init

# Fix missing build dependencies for cooltools
uv pip install cython setuptools numpy
uv pip install --no-build-isolation cooltools==0.5.1

# Lock the rest (excluding cooltools)
uv add -r prespecified_pip.txt

# Add any extra requirements
uv add -r requirements.txt

# Install Basenji source (Optional)
uv pip install -e . --no-deps
```

---

## Test the install

```bash
python -c "import basenji"
```

---

## Notes

- `prespecified_pip.txt` is extracted from the `pip` section in the original `prespecified.yml`
- `uv.lock` ensures reproducibility
- `cooltools==0.5.1` requires a manual build due to missing `pyproject.toml`

---

## Running scripts without activating env

```bash
uv run python path/to/script.py
```


