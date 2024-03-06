# Asset Registry

> The Asset Registry is an editor subsystem which gathers information about unloaded assets
> asynchronously as the editor loads. This information is stored in memory so the editor can create
> lists of assets without loading them. The information is authoritative and is kept up to date
> automatically as assets are changed in memory or files are changed on disk. The Content Browser
> is the primary consumer for this system, but it may be used anywhere in editor code.
>
> [Unreal 4.27 docs][unreal-docs-asset-register]

Some mods rely on the Asset Registry system to search for assets, like
[*Custom Overclock Framework*](https://mod.io/g/drg/m/custom-overclock-framework).
`AssetRegister.bin` seems like a way for mods to supply information to the in-game mod loading
system during initialization so that the asset registry can be augmented with information on mod
assets. As of 2024-03-03, we don't support the construction of a `AssetRegister.bin` in the
merged mod pak `mods_P.pak`. We explicitly strip out any `AssetRegister.bin` during mod asset 
merging. Since mods can contain `AssetRegister.bin` with invalid entries, it's better if we
build up `AssetRegister.bin` for the merged mod pak by parsing mod assets and possibly after
asset conflict resolution.

The plan for asset registry support in Mint is likely going to be in three steps:

1. `AssetRegister.bin` serialization and deserialization
2. Asset header information extraction
3. Asset registry construction for merged mods

## Relevant links

- Issue for asset registry support / population / merging:
  <https://github.com/trumank/mint/issues/57>.
- Asset registry Unreal docs:
  <https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ProgrammingWithCPP/Assets/Registry/>.

[unreal-docs-asset-register]: https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ProgrammingWithCPP/Assets/Registry/
