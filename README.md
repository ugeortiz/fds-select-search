# FDS Search and Selection

Working prototype for searching a Frontend Data Set while items stay selected — [LPD-109703](https://liferay.atlassian.net/browse/LPD-109703).

No build step, no server. Open `index.html` directly in a browser.

## What's here

One "Products" table with 53 items, search by name, filters, pagination and multiple selection.

- **The toolbar never changes mode.** Search, Filter and New stay available while items are selected. The selection gets its own bar underneath instead of replacing the toolbar.
- **The selection survives everything.** Searching, paging or changing the page size never drops a selected item.
- **You always know what you can't see.** The selection bar shows the total and how many selected items are outside the search or on other pages.
- **Show selected** lists the whole selection on its own (the search and filters are set aside and come back when you leave). Items you deselect there stay in place, dimmed, so rows don't jump under the cursor.
- **Selecting in bulk is per page.** The toolbar checkbox selects or deselects the visible page: checked when the whole page is selected, indeterminate when part of it is. Selecting every result across pages is out of scope here, since loading every row is too heavy on large Data Sets.
- **Clear search and Clear selection are separate.** Clearing one never touches the other.
- **Bulk actions apply to the whole selection.** Delete asks for confirmation and, when some of the selected items aren't visible, says how many and offers to review them first.

## Filtering, as in the FDS

Filtering follows the real Frontend Data Set components (FiltersDropdown, SelectionFilter, DateTimeRangeFilter, ResultsBar):

- **Filter** opens the list of filters, with a search box. Picking one opens its panel with a back arrow.
- **Selection filters** use radios (single) or checkboxes (multiple), an optional autocomplete with the chosen values as removable labels, and an Exclude toggle. Catalog, Product Type and Shippable are the ones Products has in Commerce; Status comes from the CMS.
- **Modified Date** is a From/To range and rejects a "From" after "To".
- The panel button reads **Add Filter**, **Show Results** once an active filter changes, or **Delete Filter** when every value is removed, and stays disabled when there is nothing to apply.
- The results bar shows "N Results Found for:" with a chip for the search and one per filter (first three values plus a +N badge). Clicking a chip edits that filter in place; × removes it. **Clear** resets the search and the filters, never the selection.
- **Show selected** appears as its own chip and sets the search and filters aside; you can still search or filter inside it, and they come back when you leave.

Selection changes and result counts are announced to screen readers. On narrow screens the bulk actions collapse to icons and the overflow menu.
