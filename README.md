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

To create base’s development environment, go to directory libs/base and execute:

```sh
python3 -m venv .venv

# Make the sandbox active in the current shell session
source .venv/bin/activate

# Install pinned pip first
pip install -r $(git rev-parse --show-toplevel)/pip-requirements.txt

# Install shared development dependencies and project/library-specific dependencies
pip install -r $(git rev-parse --show-toplevel)/dev-requirements.txt -r requirements.txt

# With project-specific dependencies installed, typecheck your code as follows:
pyright .
```
