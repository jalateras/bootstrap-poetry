# Bootstrap Poetry

A Python CLI application bootstrapped with modern Python packaging and tooling.

## Tech Stack

- **Python**: >=3.11
- **Package Manager**: [uv](https://github.com/astral-sh/uv) for fast Python package management
- **Build System**: [Hatchling](https://github.com/pypa/hatch) for building distributions
- **CLI Framework**: [Click](https://click.palletsprojects.com/) for command-line interfaces
- **Configuration**: [python-dotenv](https://github.com/theskumar/python-dotenv) for environment variables
- **Config Parsing**: [toml](https://github.com/uiri/toml) for TOML configuration files

### Development Tools

- **Linting**: [Ruff](https://github.com/astral-sh/ruff) for fast Python linting
- **Formatting**: [Black](https://github.com/psf/black) for code formatting
- **Testing**: [pytest](https://pytest.org/) for testing framework
- **Git Hooks**: Pre-commit hooks for code quality

## Getting Started

### Prerequisites

- Python 3.11 or higher
- [uv](https://github.com/astral-sh/uv) package manager

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd bootstrap-poetry
   ```

2. Install dependencies:
   ```bash
   make install
   ```

3. For development, install with dev dependencies:
   ```bash
   make install-dev
   ```

4. Set up git hooks:
   ```bash
   make hooks
   ```

### Usage

Run the CLI application:
```bash
python cli.py --help
```

Check version:
```bash
python cli.py version
```

### Development

#### Available Make Commands

- `make install` - Install production dependencies
- `make install-dev` - Install development dependencies
- `make sync` - Sync dependencies
- `make lint` - Run linter (Ruff)
- `make lint-fix` - Run linter with auto-fix
- `make format` - Format code with Black
- `make version` - Display application version
- `make hooks` - Install git pre-commit hooks

#### Code Quality

The project uses automated code quality tools:

- **Ruff** for linting and import sorting
- **Black** for consistent code formatting
- **Pre-commit hooks** to ensure code quality before commits

Run linting and formatting:
```bash
make lint
make format
```

## Using as a Template

This project can be used as a template to bootstrap new Python CLI applications. Here's how to set up a new project:

### Method 1: Fresh Git Repository (Recommended)

1. Clone this template:
   ```bash
   git clone <this-repository-url> my-new-project
   cd my-new-project
   ```

2. Remove the existing git history and start fresh:
   ```bash
   rm -rf .git
   git init
   git add .
   git commit -m "Initial commit from bootstrap-poetry template"
   ```

3. Add your new remote repository:
   ```bash
   git remote add origin <your-new-repository-url>
   git push -u origin main
   ```

### Method 2: Change Git Remote

If you want to keep the commit history:

1. Clone this template:
   ```bash
   git clone <this-repository-url> my-new-project
   cd my-new-project
   ```

2. Change the remote URL:
   ```bash
   git remote set-url origin <your-new-repository-url>
   git push -u origin main
   ```

### Customization Checklist

After setting up the repository, customize these files for your project:

- [ ] **pyproject.toml**: Update `name`, `description`, `authors`, and `email`
- [ ] **Package directory**: Rename `bootstrap_poetry/` to `your_project_name/`
- [ ] **cli.py**: Update imports to reference your new package name
- [ ] **Makefile**: Update `CLI` variable if you rename cli.py
- [ ] **README.md**: Replace this content with your project's documentation
- [ ] **main.py**: Replace placeholder content with your application logic

### Example Customization

For a project called "my-awesome-cli":

1. Rename the package directory:
   ```bash
   mv bootstrap_poetry my_awesome_cli
   ```

2. Update pyproject.toml:
   ```toml
   [project]
   name = "my-awesome-cli"
   description = "My awesome CLI application"
   authors = [
       {name = "Your Name", email = "your.email@example.com"}
   ]
   ```

3. Update imports in cli.py:
   ```python
   from my_awesome_cli.version import version
   ```

4. Update the wheel packages in pyproject.toml:
   ```toml
   [tool.hatch.build.targets.wheel]
   packages = ["my_awesome_cli"]
   ```

## Project Structure

```
bootstrap-poetry/
├── bootstrap_poetry/          # Main package
│   └── version.py            # Version management
├── cli.py                    # CLI entry point
├── main.py                   # Main application
├── pyproject.toml           # Project configuration
├── uv.lock                  # Lock file for dependencies
├── Makefile                 # Build automation
├── hooks/                   # Git hooks
│   └── pre-commit          # Pre-commit hook script
└── README.md               # This file
```