# fyso-extensions

The official catalog of extensions for the Fyso Agentic Framework. Projects read it by
default (`project/marketplaces.yaml`) and show its entries in the panel's
**Apps → Marketplace** and in `mise run ext:search`.

## Add an extension

1. Create the extension from the framework's starter
   (`framework/extensions/_template`, see its README) in its own repo, and tag a release
   (`v1.0.0`).
2. Open a PR here adding one entry to `marketplace.yaml`:

   ```yaml
   - id: foo
     src: gh:fyso-dev/fyso-ext-foo
     name: {es: Foo, en: Foo}
     description: {es: …, en: …}
     tags: []
   ```

Versions are read live from the extension repo's tags; never list them here. Format and
behavior: `docs/extensions-contract.md` §8 and ADR 0002 in `fyso-dev/agentic-framework`.

## Private extensions and compatibility

A catalog entry may reference a private repository. Installation and version discovery
use the caller's normal GitHub credentials; repository read access is required.

`biz` requires framework panel extension API v1 and connection hooks (framework PR
[fyso-dev/agentic-framework#14](https://github.com/fyso-dev/agentic-framework/pull/14)).
The extension validates compatibility before installing its slots.
