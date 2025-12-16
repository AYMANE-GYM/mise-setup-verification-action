# Mise Setup & Verification Action

![GitHub Release](https://img.shields.io/github/v/release/Baneeishaque/mise-setup-verification-action)
![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/Baneeishaque/mise-setup-verification-action/test.yml)
![License](https://img.shields.io/github/license/Baneeishaque/mise-setup-verification-action)

A GitHub Composite Action to set up [mise](https://mise.jdx.dev/), install tools, and verify installation integrity using a customizable verification script.

This action wraps `jdx/mise-action` with an additional layer of verification to ensure your CI/CD environment is exactly as deterministic as you expect.

## Features

- 🛠 **Setup Mise**: Installs a specific version of `mise`.
- 📦 **Install Tools**: Automatically installs tools defined in `mise.toml`.
- ✅ **Verify Installation**: Runs a custom verification script to ensure the tool is available and matches the expected version.
- 🚀 **Caching**: Built-in caching for faster workflows.

## Usage

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Python via Mise
        uses: Baneeishaque/mise-setup-verification-action@v1
        with:
          mise_version: '2025.12.9'
          working_directory: '.' 
          tool_name: 'python' 
          version_command: 'python -V'
```

## Inputs

| Input | Description | Required | Default |
| :--- | :--- | :---: | :---: |
| `mise_version` | Version of mise to install. | **Yes** | - |
| `working_directory` | Directory containing `mise.toml`. | **Yes** | - |
| `tool_name` | Name of the tool to verify (e.g., `python`, `node`). | **Yes** | - |
| `version_command` | Command to output version (e.g., `python -V`). | **Yes** | - |
| `install` | Whether to run `mise install`. | No | `true` |
| `cache` | Whether to enable caching. | No | `true` |
| `mise_file` | Name of the mise configuration file. | No | `mise.toml` |

## Example `mise.toml`

```toml
[tools]
python = "3.12"
node = "20"
```

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

MIT © [Banee Ishaque K](LICENSE)
