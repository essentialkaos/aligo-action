<p align="center"><a href="#readme"><img src="https://gh.kaos.st/aligo-action.svg"/></a></p>

<br/>

Action for checking scripts with [_Aligo_](https://kaos.sh/aligo).

### Usage

Create file `.github/workflows/aligo.yml`.

Add next code to it:

```yml
name: CI

on:
  push:
    branches: [master, develop]
  pull_request:
    branches: [master]

jobs:
  Aligo:
    name: Aligo
    runs-on: ubuntu-latest

    env:
      SRC_DIR: src/github.com/${{ github.repository }}

    steps:
      - name: Set up Go
        uses: actions/setup-go@v2
        with:
          go-version: '1.17.x'
        id: go

      - name: Setup PATH
        run: |
          echo "GOPATH=${{ github.workspace }}" >> "$GITHUB_ENV"
          echo "GOBIN=${{ github.workspace }}/bin" >> "$GITHUB_ENV"
          echo "${{ github.workspace }}/bin" >> "$GITHUB_PATH"

      - name: Checkout
        uses: actions/checkout@v3
        with:
          path: ${{env.SRC_DIR}}

      - name: Check Golang sources with Aligo
        uses: essentialkaos/aligo-action@v1
        with:
          path: ${{env.SRC_DIR}}
          files: ./...

```

### Options

| Option | Description | Value |
|--------|-------------|--------|
| `path` | Path to directory with sources | _Path_ |
| `files` | Files or directories to check | _List_ |
| `version` | Aligo version | _Version in semver notation_ |

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
