# Compact Add to Cart – Changelog

- Removed grid `MutationObserver` and `:has()` CSS rule to avoid layout thrashing and skeleton stalls.
- Added idempotent `applyCompactState` using per-card `ResizeObserver`, debounced resize handler, and `ON_PRODUCT_LIST_UPDATED` hook for lazy-loaded products.
