# Run Swellow CLI GitHub Action

[![CI](https://github.com/franciscoabsampaio/action-swellow/actions/workflows/ci.yaml/badge.svg)](https://github.com/franciscoabsampaio/action-swellow/actions/workflows/ci.yaml)
[![GitHub release](https://img.shields.io/github/v/release/franciscoabsampaio/action-swellow)](https://github.com/franciscoabsampaio/action-swellow/releases/latest)
[![License](https://img.shields.io/github/license/franciscoabsampaio/action-swellow)](./LICENSE)

Easily run the [Swellow CLI](https://github.com/franciscoabsampaio/swellow) inside your GitHub Actions workflows.
This action automatically downloads the correct binary for your platform, extracts it, and executes your desired command with minimal setup.

## Features

* ✅ Always pulls the **latest release** by default (or pin a specific version).
* ✅ Supports **Linux, macOS (Apple Silicon), and Windows**.
* ✅ Pass connection strings, migration directories, and custom arguments seamlessly.
* ✅ Ideal for running database migrations in CI/CD pipelines.

---

## Usage

```yaml
jobs:
  migrate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Swellow migrations
        uses: franciscoabsampaio/swellow-action@v1
        with:
          command: up
          connection-string: ${{ secrets.DATABASE_URL }}
          migrations-directory: ./migrations
          verbose: true
```

---

## Inputs

| Name                   | Required | Default        | Description                                              |
| ---------------------- | -------- | -------------- | -------------------------------------------------------- |
| `command`              | ✅        | `up`           | Swellow command to execute (`up`, `down`, etc.)          |
| `connection-string`    | ✅        | `""`           | Database connection string                               |
| `migrations-directory` | ❌        | `./migrations` | Directory containing migration files                     |
| `args`                 | ❌        | `""`           | Additional arguments to pass to Swellow                  |
| `version`              | ✅        | `latest`       | CLI version to download (GitHub release tag (`vX.Y.Z`) or `latest`) |
| `verbose`              | ❌        | `false`        | Enable verbose output                                    |

---

## License

This action is licensed under the Apache 2.0 License.
