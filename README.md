## Customize

Installation of Node and Python is controlled by the `.env` file.

It acts as a single source of truth for Node and Python versions for all Docker containers.

### `NODE_VERSION: "[value]"`

Possible values:
- node: installs latest Node version
- "20": installs Node 20
- "": skips installation of Node

Installing Node also installs npm. Yarn is not installed currently.

Refer to `nvm` documentation for valid Node versions.

### `PYTHON_VERSION: "[value]"`

Possible values:
- "3": installs the latest minor.patch Python version in major version 3
- "3.2": installs the latest patch Python version in major.minor version 3.2
- "3.2.1": installs the specific Python version
- "": skips installation of Node

Refer to `pyenv` documentation for valid Python version.


## Questions

**How is `nvm` installed**

Refer to `.devcontainer/Dockerfile`.

```
RUN curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
```

The `nvm` install script updates `~/.bashrc` and installs the Node version specified by `NODE_VERSION` in `.env`. If no version is specified, it will not install Node.

Because the script automatically updates `~/.bashrc`, we do not have to do anything else in the Dockerfile.
