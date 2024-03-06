# `AssetRegister.bin` serialization and deserialization

Current interpretation of the `AssetRegister.bin` file format:

![`AssetRegister.bin` format](img/AssetRegister.bin-format.svg)

Note that this interpretation is not 100% "spec-compliant" with Unreal's actual asset registry
(de-)serialization, since it purposefully contains some omissions and simplications so that the
format is sufficient for mint use cases.
