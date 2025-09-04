# ATC layout switch on collection cards

- **Wrap signal:** reuse `.collection-qty-group.is-wrapped` (set when the double quantity button drops under the input). The script also toggles `.is-qty-wrapped` on the surrounding `.collection-form__actions` container.
- **Where:** CSS in `collection-quick-add.css` listens to `.is-qty-wrapped` to switch the add to cart button between inline auto-width and stacked full-width. Logic lives in `updateQtyGroupLayout` within `collection-quick-add.js`.
- **Manual checks:**
  - wide card: quantity group and "Adaugă încă" on one line, Add to Cart shrinks to text width and sticks to the right.
  - narrow card / long labels: quantity group wraps, Add to Cart spans full width on next row.
  - resizing back restores inline state automatically.
  - spinner, cart events, min/step/max and double-qty behaviour unaffected.
