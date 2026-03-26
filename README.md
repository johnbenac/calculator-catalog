# calculator-catalog

Third-party OurBox application catalog for the [calculator](https://github.com/johnbenac/calculator-apps) app.

Follows the [OurBox application catalog repository pattern](https://github.com/techofourown/sw-ourbox-os/blob/main/docs/reference/app-authoring-guide.md).
Tooling scripts are pulled automatically at CI time via `bootstrap.sh` — they are not checked in.

## Apps

| App UID | Display name | Service | Port | Hostname |
|---|---|---|---|---|
| `johnbenac/calculator` | Calculator | `calculator` | 80 | `calc.{box_host}` |

## Image sources

Images published by [`johnbenac/calculator-apps`](https://github.com/johnbenac/calculator-apps):

- `ghcr.io/johnbenac/calculator-apps/calculator:latest`

## Catalog bundle

On every push to `main`, the publish workflow:

1. runs `bootstrap.sh` to pull shared tooling scripts from the catalog-tooling OCI artifact
2. resolves all image refs to digest-pinned refs
3. renders `catalog.json + images.lock.json + profile.env + manifest.env` into
   `dist/application-catalog-bundle.tar.gz`
4. publishes the bundle to `ghcr.io/johnbenac/calculator-catalog`
5. updates the catalog index at `:catalog-amd64`

To use this catalog, enter the following ref at the installer's catalog selection step:

```
ghcr.io/johnbenac/calculator-catalog:catalog-amd64
```

## References

- [App authoring guide](https://github.com/techofourown/sw-ourbox-os/blob/main/docs/reference/app-authoring-guide.md)
- [Application catalog repository contract](https://github.com/techofourown/sw-ourbox-os/blob/main/docs/reference/application-catalog-repository-contract.md)
- [Application catalog repo template](https://github.com/techofourown/sw-ourbox-os/tree/main/templates/application-catalog-repo)
- [Calculator apps repo](https://github.com/johnbenac/calculator-apps)
