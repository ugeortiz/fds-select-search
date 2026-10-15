# FDS Search and Selection

Working prototype for searching a Frontend Data Set while items stay selected — [LPD-109703](https://liferay.atlassian.net/browse/LPD-109703).

No build step, no server. Open `index.html` directly in a browser.

## What's here

One "Products" table with 53 items, search by name, pagination and multiple selection.

- **The toolbar never changes mode.** Search, Filter and New stay available while items are selected. The selection gets its own bar underneath instead of replacing the toolbar.
- **The selection survives everything.** Searching, paging or changing the page size never drops a selected item.
- **You always know what you can't see.** The selection bar shows the total and how many selected items are outside the search or on other pages.
- **Show selected** lists the whole selection on its own (the search is set aside and comes back when you leave). Items you deselect there stay in place, dimmed, so rows don't jump under the cursor.
- **Selecting in bulk is per page.** The toolbar checkbox selects or deselects the visible page: checked when the whole page is selected, indeterminate when part of it is. Selecting every result across pages is out of scope here, since loading every row is too heavy on large Data Sets.
- **Clear search and Clear selection are separate.** Clearing one never touches the other.
- **Bulk actions apply to the whole selection.** Delete asks for confirmation and, when some of the selected items aren't visible, says how many and offers to review them first.

Selection changes and result counts are announced to screen readers. On narrow screens the bulk actions collapse to icons and the overflow menu.
