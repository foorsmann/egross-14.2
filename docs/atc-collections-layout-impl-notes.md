# ATC collections layout implementation notes

- **Wrap signal**: `.is-qty-wrapped` toggled on the action container by `updateQtyGroupLayout` (`assets/collection-quick-add.js` lines 681-693). It compares the `offsetTop` of `.collection-double-qty-btn` to the quantity input and toggles the class. `watchQtyGroupLayout` re-evaluates on `resize` and on DOM mutations; `initAll` invokes it on `DOMContentLoaded`, `shopify:section:load`, `shopify:cart:updated`, and `shopify:product:updated`, ensuring runtime accuracy.

- **State A (one row)**: When `.collection-form__actions` lacks `.is-qty-wrapped`, `.collection-add-to-cart` is forced to `width:auto`, `margin-top:0`, `margin-left:auto`, and `flex-grow:0` (`assets/collection-quick-add.css` lines 96-101). The quantity wrapper is relaxed to `flex:1 1 auto` so the group and button share a single line.

- **State B (wrapped)**: With `.is-qty-wrapped` present, default utility classes (`w-full`, `mt-4`) keep the add-to-cart button at `width:100%` with `margin-top:1rem`, preserving the existing vertical spacing.

- **Events monitored**: Layout is recalculated on `resize`, `DOMContentLoaded`, `shopify:section:load`, `shopify:cart:updated`, `shopify:product:updated`, and MutationObserver callbacks for `.sf-collection-list` / `.collection-listing`.

- **Manual testing**: Checked cards at ~1280 px (inline mode), ~768 px (transition point), ~360 px (stacked mode), and within a product slider. In all cases the add-to-cart button switched modes without affecting spinner, cart events or quantity logic.
