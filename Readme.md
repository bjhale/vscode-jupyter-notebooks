# Jupyter Multi-Language Notebook Template for VSCode

A VS Code Dev Container environment with integrated Jupyter support for Python, R, and TypeScript/JavaScript (via Deno). This template provides a ready-to-use data science workspace with popular libraries pre-installed, all running directly within VS Code.

## Features

- 🐍 **Python 3** - NumPy, Pandas, Matplotlib, SciPy, and more
- 📊 **R** - Complete R environment with data analysis packages
- 🦕 **TypeScript/JavaScript** - Deno kernel for modern JavaScript/TypeScript notebooks
- 📓 **Native Jupyter Integration** - Run notebooks directly in VS Code
- 🤖 **GitHub Copilot Ready** - AI pair programming support pre-configured

## Prerequisites

- **Visual Studio Code** - [Download here](https://code.visualstudio.com/)
- **Docker Desktop** (Windows/Mac) or **Docker Engine** (Linux) - [Get Docker](https://docs.docker.com/get-docker/)
- **Dev Containers Extension** for VS Code - [Install from Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Setup

1. **Clone this repository** to your local machine:
   ```bash
   git clone https://github.com/bjhale/vscode-jupyter-notebooks.git
   cd vscode-jupyter-notebooks
   ```

2. **Open in VS Code:**
   ```bash
   code .
   ```

3. **Reopen in Container:**
   - VS Code will detect the dev container configuration
   - Click **"Reopen in Container"** when prompted
   - Or use Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`) → **"Dev Containers: Reopen in Container"**

4. **Wait for setup to complete** (~2-5 minutes on first run):
   - Docker will build the container
   - VS Code will install extensions inside the container
   - Jupyter server will start automatically

5. **Start coding!**
   - Open any `.ipynb` file from the `tests/` folder
   - Or create a new notebook: Command Palette → **"Create: New Jupyter Notebook"**

### Verifying the Setup

1. **Check Extensions:**
   - Jupyter extension should be active (icon in left sidebar)
   - Python extension should be active
   - GitHub Copilot (if you have access)

2. **Test Jupyter Server:**
   - Open Terminal: `` Ctrl+` `` or `View → Terminal`
   - Run: `jupyter notebook list`
   - You should see a server running on port 8888

3. **Test Notebooks:**
   - Open [tests/test-python.ipynb](tests/test-python.ipynb)
   - Click **"Run All"** or run cells individually
   - You should see output rendered inline


## Usage

### Working with Notebooks in VS Code

**Creating a New Notebook:**
1. Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`) → **"Create: New Jupyter Notebook"**
2. Select your kernel:
   - **Python 3 (ipykernel)** - for Python
   - **R** - for R code
   - **Deno** - for TypeScript/JavaScript
3. Start writing code in cells

**Running Cells:**
- Run single cell: Click the ▶️ icon or `Shift+Enter`
- Run all cells: Click **"Run All"** at the top
- Run above: Right-click cell → **"Run Above"**
- Run below: Right-click cell → **"Run Below"**

**Keyboard Shortcuts:**
- `Shift+Enter` - Run cell and move to next
- `Ctrl+Enter` - Run cell and stay
- `Alt+Enter` - Run cell and insert below
- `A` - Insert cell above (in command mode)
- `B` - Insert cell below (in command mode)
- `DD` - Delete cell (in command mode)
- `M` - Change to markdown cell
- `Y` - Change to code cell

### Testing the Installation

The `tests/` directory contains sample notebooks:

- [tests/test-python.ipynb](tests/test-python.ipynb) - Python examples with matplotlib
- [tests/test-r.ipynb](tests/test-r.ipynb) - R examples with base plotting
- [tests/test-typescript.ipynb](tests/test-typescript.ipynb) - TypeScript with Observable Plot

Open and run these notebooks to verify each kernel works correctly.

### Installing Additional Packages

**Python Packages:**

From within a notebook cell:
```python
%pip install package-name
```

Or using the terminal:
```bash
pip install package-name
```

**R Packages:**

From within an R notebook cell:
```r
install.packages("package-name")
```

**TypeScript/Deno Packages:**

Import directly from npm (no installation needed):
```typescript
import * as pkg from "npm:package-name";
```

### Working with Your Own Projects

1. **Your files are automatically synced** - Everything in the workspace folder is available in the container

2. **Create notebooks anywhere** in the workspace directory structure

3. **Access data files** - Place CSV, JSON, or other data files in the workspace and reference them directly:
   ```python
   import pandas as pd
   df = pd.read_csv('data/myfile.csv')
   ```

4. **Version control** - The `.git` folder is accessible, so you can use Git normally within VS Code

### Using GitHub Copilot

This template pre-configures GitHub Copilot for AI-assisted coding:

1. Ensure you have a [GitHub Copilot subscription](https://github.com/features/copilot)
2. Sign in to GitHub in VS Code (bottom-left status bar)
3. Start typing in a code cell - Copilot will suggest completions
4. Use Copilot Chat: Click the chat icon or `Ctrl+Shift+I`

### Switching Python Interpreters

The container includes multiple Python environments:

1. Command Palette → **"Python: Select Interpreter"**
2. Choose from available interpreters
3. The default is the base conda environment with all data science packages


## Configuration

### Dev Container Settings

The dev container configuration is in [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json).

**Key settings:**
- **Container name**: "Jupyter Notebooks"
- **Workspace folder**: `/home/jovyan/work`
- **Port forwarding**: Port 8888 (Jupyter server)
- **Pre-installed extensions**: Jupyter, Python, GitHub Copilot
- **Jupyter token**: `123`

### Customizing Extensions

Add or remove VS Code extensions by editing [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json):

```json
"customizations": {
    "vscode": {
        "extensions": [
            "ms-toolsai.jupyter",
            "ms-python.python",
            "github.copilot",
            "github.copilot-chat",
            "your-extension-id"
        ]
    }
}
```

Then rebuild the container: Command Palette → **"Dev Containers: Rebuild Container"**


Rebuild the container to apply changes.

### Adding System Packages or Libraries

Edit [docker/Dockerfile](docker/Dockerfile):

```dockerfile
# Add system packages
USER root
RUN apt-get update && apt-get install -y \
    package-name \
    another-package
USER ${NB_UID}

# Add Python packages globally
RUN pip install package-name

# Add R packages globally  
RUN R -e "install.packages('package-name')"
```

Then rebuild: Command Palette → **"Dev Containers: Rebuild Container"**

## Additional Resources

### Documentation
- [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers)
- [Jupyter in VS Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
- [Jupyter Documentation](https://docs.jupyter.org/)
- [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/)
- [Deno Documentation](https://deno.land/manual)
- [R Documentation](https://www.r-project.org/other-docs.html)

### Learning Resources
- [VS Code Jupyter Tutorial](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
- [R for Data Science](https://r4ds.had.co.nz/)

### Community
- [VS Code Dev Containers Issues](https://github.com/microsoft/vscode-remote-release/issues)
- [Jupyter Community](https://jupyter.org/community)

## License

This template is provided as-is for educational and development purposes.
