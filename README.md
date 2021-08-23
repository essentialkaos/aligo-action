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
      - name: Code checkout
        uses: actions/checkout@v2

      - name: Check dockerfiles with Aligo
        uses: essentialkaos/aligo-action@v1
        with:
          path: ./...

```

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
