---
name: Manage Typeface brand kits and styles
description: List, create, and train brand kits and their image/text/logo
  styles so generated content stays on-brand.
api: openapi/typeface-api-openapi.json
operations:
  - queryBrandsInAccount
  - createBrandKitInAccount
  - deleteBrandKitInAccount
  - getStyleinBrandkit
  - createStyleinBrandkit
  - uploadImageInBrandKitStyle
  - trainBrandKitImagestyle
generated: '2026-07-21'
method: generated
---

# Manage Typeface brand kits and styles

1. Authenticate (see `skills/typeface-generate-content.md`, step 1).
2. **List brand kits** in a team with `queryBrandsInAccount`.
3. **Create** one with `createBrandKitInAccount`; remove with
   `deleteBrandKitInAccount`.
4. **Styles.** List existing styles of a given type (Image / Text / Logo) with
   `getStyleinBrandkit`; create styles for content generation with
   `createStyleinBrandkit`.
5. **Images.** Upload brand images to a style with `uploadImageInBrandKitStyle`
   and train the image style with `trainBrandKitImagestyle`.
6. Reference the brand kit (and optionally audiences and layouts) in
   batch-generation requests so output adheres to brand guidelines.

All calls require `Authorization: Bearer <JWT>`; responses are HAL-linked.
