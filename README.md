# cURL Action

![GitHub Action](https://img.shields.io/github/actions/workflow/status/your-username/generic-rest-client-curl/main.yml?branch=main)
![License](https://img.shields.io/github/license/your-username/generic-rest-client-curl)

A simple, lightweight GitHub Action to perform REST API calls using `curl`.

## Features

- Supports **GET**, **POST**, **PUT**, **DELETE**, etc.
- Custom HTTP headers (passed as JSON).
- Optional request body.
- Timeout configuration.
- No Docker, No Node.js dependencies — pure Bash and cURL.

## Inputs

| Input | Description | Required | Default |
|:------|:------------|:---------|:--------|
| `url` | URL to call. | ✅ | - |
| `method` | HTTP method to use. | ✅ | `GET` |
| `headers` | Optional JSON string of headers. | ❌ | - |
| `body` | Optional JSON string for request body. | ❌ | - |
| `timeout` | Timeout in seconds. | ❌ | `10` |

## Outputs

| Output | Description |
|:-------|:------------|
| `status_code` | HTTP status code from the response. |
| `response_body` | Response body content. |

## Example Usage

```yaml
name: Example Call API
on:
  workflow_dispatch:
    inputs:
      url:
        description: 'Target URL'
        required: true
      method:
        description: 'HTTP Method'
        required: true
        default: 'GET'

jobs:
  call-api:
    runs-on: ubuntu-latest
    steps:
      - name: Call API
        uses: your-username/generic-rest-client-curl@v1
        with:
          url: ${{ github.event.inputs.url }}
          method: ${{ github.event.inputs.method }}
          headers: '{"Authorization": "Bearer ${{ secrets.API_TOKEN }}"}'
```

## Requirements

- `curl` (preinstalled on GitHub-hosted runners)
- `jq` (for parsing JSON headers)

## License

[MIT License](LICENSE)
