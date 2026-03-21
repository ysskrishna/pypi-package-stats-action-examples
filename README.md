# 🚀 PyPI Package Stats — Example Workflows

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-PyPI%20Package%20Stats-blue?logo=github)](https://github.com/marketplace/actions/pypi-package-stats)
[![pypi-package-stats GitHub Action](https://img.shields.io/badge/GitHub-pypi--package--stats--action-blue.svg)](https://github.com/ysskrishna/pypi-package-stats-action)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![pypi-package-stats Documentation](https://img.shields.io/badge/docs-ysskrishna.github.io%2Fpypi--package--stats-blue.svg)](https://ysskrishna.github.io/pypi-package-stats/)



Ready-to-use GitHub Actions workflows for integrating [`ysskrishna/pypi-package-stats-action`](https://github.com/ysskrishna/pypi-package-stats-action) into CI pipelines.


## Quick Start

```yaml
- uses: ysskrishna/pypi-package-stats-action@v1
  id: stats
  with:
    package-name: 'requests'

- run: echo "Downloads last month: ${{ steps.stats.outputs.last-month-downloads }}"
```

> **Note:** The `id` field (e.g. `id: stats`) is required to reference step outputs. If you only need the JSON file or Job Summary, you can omit it.

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `package-name` | PyPI package name to fetch statistics for | Yes | — |
| `output-path` | File path to write the JSON stats output | No | `stats.json` |

## Outputs

| Output | Description |
|--------|-------------|
| `stats-json` | Full JSON string of package statistics |
| `name` | Package name |
| `version` | Current package version on PyPI |
| `last-day-downloads` | Downloads in the last day |
| `last-week-downloads` | Downloads in the last week |
| `last-month-downloads` | Downloads in the last month |

## Accessing Stats

There are three ways to access the fetched statistics:

1. **Step outputs** — Reference outputs like `steps.<id>.outputs.last-month-downloads` in subsequent steps. Requires `id` on the action step.
2. **JSON file** — Stats are written to the `output-path` file (default: `stats.json`). Useful for artifacts or downstream processing.
3. **Job Summary** — A Markdown stats table is automatically added to the workflow run's Summary page. No configuration needed.

## JSON Output Schema

The `stats-json` output and the file written to `output-path` contain the following structure:

```json
{
  "package": {
    "name": "requests",
    "version": "2.32.3",
    "upload_time": "2024-05-29",
    "description": "Python HTTP for Humans.",
    "author": "Kenneth Reitz",
    "license": "Apache-2.0",
    "home_page": "https://requests.readthedocs.io",
    "pypi_url": "https://pypi.org/project/requests/"
  },
  "downloads": {
    "last_day": 2500000,
    "last_week": 17500000,
    "last_month": 75000000,
    "last_180d": 450000000
  },
  "python_versions": [
    { "version": "3.12", "downloads": 5000000, "percentage": 35.0 },
    { "version": "3.11", "downloads": 4000000, "percentage": 28.0 }
  ],
  "operating_systems": [
    { "os": "Linux", "downloads": 12000000, "percentage": 68.0 },
    { "os": "Windows", "downloads": 3500000, "percentage": 20.0 },
    { "os": "Darwin", "downloads": 2000000, "percentage": 12.0 }
  ]
}
```

## Usage Examples

| Example | Description |
|---------|-------------|
| [Basic — Print Stats](https://github.com/ysskrishna/pypi-package-stats-action-examples/blob/main/.github/workflows/basic-print-stats.yml) | Fetch and print download stats |
| [Check Download Threshold](https://github.com/ysskrishna/pypi-package-stats-action-examples/blob/main/.github/workflows/check-download-threshold.yml) | Warn if monthly downloads fall below a threshold |
| [Custom Output Path](https://github.com/ysskrishna/pypi-package-stats-action-examples/blob/main/.github/workflows/custom-output-path.yml) | Write stats JSON to a custom file path |
| [Save Stats as Artifact](https://github.com/ysskrishna/pypi-package-stats-action-examples/blob/main/.github/workflows/save-stats-artifact.yml) | Save stats as a downloadable GitHub Actions artifact |


## License

MIT © [Y. Siva Sai Krishna](https://github.com/ysskrishna) — see [LICENSE](LICENSE) for details.

## Credits

Examples for [pypi-package-stats-action](https://github.com/ysskrishna/pypi-package-stats-action). Built on [pypi-package-stats](https://github.com/ysskrishna/pypi-package-stats).

---

<p align="left">
  <a href="https://github.com/ysskrishna">Author's GitHub</a> •
  <a href="https://linkedin.com/in/ysskrishna">Author's LinkedIn</a> •
  <a href="https://github.com/marketplace/actions/pypi-package-stats">GitHub Marketplace</a> •
  <a href="https://github.com/ysskrishna/pypi-package-stats-action">pypi-package-stats-action</a> •
  <a href="https://github.com/ysskrishna/pypi-package-stats">pypi-package-stats Documentation</a>
</p>
