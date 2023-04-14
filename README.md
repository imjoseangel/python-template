# Python Template Repository

This python monorepo template has the following structure:

```sh
├── .flake8
├── dev-requirements.txt
├── pip-requirements.txt
├── pyproject.toml
├── libs/
└── projects/
```

With this setup, you format and lint code deterministically locally and on the CI with:

```sh
python3 -m venv .venv

# Make the sandbox active in the current shell session
source .venv/bin/activate

# Install pinned pip first
pip install -r pip-requirements.txt

# Install shared development dependencies, in a second step
# to use the pinned pip version
pip install -r dev-requirements.txt

# Black, Flake8, and isort are now available. Use them as follows:
black --check .
flake8 .
isort --check-only .
```
