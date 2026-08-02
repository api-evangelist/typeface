---
name: Manage Typeface assets and tag taxonomy
description: Search, create, and update assets in the asset hub, and maintain
  the tag taxonomy plus per-asset tag metadata.
api: openapi/typeface-api-openapi.json
operations:
  - searchAssets
  - createAssetInAssetCatalog
  - getAssetInAssetCatalog
  - updateAssetInAssetCatalog
  - deleteAssetInAssetCatalog
  - getMetadata
  - patchMetadata
  - createTags
  - searchTags
  - getTag
  - patchTag
  - deleteTag
generated: '2026-07-21'
method: generated
---

# Manage Typeface assets and tag taxonomy

1. Authenticate (see `skills/typeface-generate-content.md`, step 1).
2. **Find assets.** `searchAssets` is the unified search across a team (and
   organization) with various filters.
3. **CRUD assets** in the asset catalog with `createAssetInAssetCatalog`,
   `getAssetInAssetCatalog`, `updateAssetInAssetCatalog`,
   `deleteAssetInAssetCatalog`.
4. **Tag metadata.** Read an asset's tags with `getMetadata`; apply JSON
   Patch-style add/replace/remove operations with `patchMetadata`.
5. **Taxonomy.** Create tags in bulk with `createTags` (each tag processed
   independently), browse with `searchTags`, inspect with `getTag`, rename or
   move with `patchTag` (paths `/name`, `/displayName`), and remove with
   `deleteTag` — deleting a tag also deletes its child tags.
6. Uploaded and updated asset images emit `image.uploaded` / `image.updated` /
   `image.deleted` webhooks (see `asyncapi/typeface-webhooks.yml`).
