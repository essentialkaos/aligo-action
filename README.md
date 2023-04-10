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

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Set up Go
        uses: actions/setup-go@v2
        with:
          go-version: '1.18.x'

      - name: Check Golang sources with Aligo
        uses: essentialkaos/aligo-action@v2
        with:
          files: ./...

```

### Options

| Option | Description | Value |
|--------|-------------|--------|
| `files` | Files or directories to check | _List_ |
| `path` | Path to directory with sources | _Path_ |
| `version` | Aligo version | _Version in semver notation_ |

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
