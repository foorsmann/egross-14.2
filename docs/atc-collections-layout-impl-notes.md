# ATC collections layout implementation notes

## Wrap signal
- Uses `.is-qty-wrapped` on `.collection-form__actions`.
- Toggled by comparing `offsetTop` of `.collection-add-to-cart` and the `.collection-qty-group` inside `updateQtyGroupLayout`.
- The layout check runs on `DOMContentLoaded`, window `resize`, `shopify:section:load`, `shopify:cart:updated`, `shopify:product:updated`, `cart:updated`, `product:updated`, and any DOM changes observed in collection lists.

## Styles
- **State A (single row)**: container lacks `.is-qty-wrapped`.
  - `.collection-add-to-cart` gets `width: auto`, `margin-top: 0`, and `margin-left: auto` to align right.
- **State B (wrapped)**: container has `.is-qty-wrapped`.
  - `.collection-add-to-cart` returns to `width: 100%` with original top margin preserved.

## Manual checks
- Verified live resize at ~1440px, ~1024px, and ~480px widths.
- Confirmed ATC stays right-aligned on single row and expands full width when wrapped.
- Tested inside a product card slider to ensure no regressions.
