# MSRV

> Read MSRV from package or workspace manifest.

## Usage

```yml
jobs:
  read_msrv:
    name: Read MSRV
    uses: actions-rust-lang/msrv/.github/workflows/msrv.yml@main

  build_and_test:
    needs:
      - read_msrv

    strategy:
      fail-fast: false
      matrix:
        version:
          - { name: msrv, version: "${{ needs.read_msrv.outputs.msrv }}" }
          - { name: stable, version: stable }
```

## Drawbacks

- Assumes all packages in workspace have same MSRV.
