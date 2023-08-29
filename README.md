# Hayagriva

> Modified version of [hayagriva](https://github.com/typst/hayagriva) that replaces the chicago-author-date style with APA style text citations.

## Modifications
- `#cite(key)` now returns APA style text citations
    - "," after author names (Lastname 2023) => (Lastname, 2023)
    - "et al." after 3+ authors (Lastname1, Lastname2, Lastname3 2023) => (Lastname1, et al., 2023)
    - "and" replaced by "&" (Lastname1 and Lastname2 2023) => (Lastname1 & Lastname2, 2023)

All that is happening inside the `src/style/chicago/author_date.rs` and the `src/style/chicago/mod.rs` files.
So hayagriva still thinks it is using the chicago style.

I know to little rust to make a propper implementation, but i need APA citations for my bachelor thesis. 


