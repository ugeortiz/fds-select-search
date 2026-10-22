# FDS Search and Selection

Working prototype for searching a Frontend Data Set while items stay selected — [LPD-109703](https://liferay.atlassian.net/browse/LPD-109703).

No build step, no server. Open `index.html` directly in a browser.

## What's here

One "Products" table with 53 items, search by name, filters, pagination and multiple selection.

- **The toolbar never changes mode.** Search, Filter and New stay available while items are selected. The selection gets its own bar underneath instead of replacing the toolbar.
- **The selection survives everything.** Searching, paging or changing the page size never drops a selected item.
- **Selecting in bulk is per page.** The toolbar checkbox selects or deselects the visible page: checked when the whole page is selected, indeterminate when part of it is. Selecting every result across pages is out of scope here, since loading every row is too heavy on large Data Sets.
- **Clear in the results bar and Clear in the selection bar are separate.** Clearing the search and filters never touches the selection, and vice versa.
- **Bulk actions apply to the whole selection.** The Delete Entries confirmation warns how many of the selected entries aren't on screen (on other pages, or outside the current search and filters).

Not in this iteration: a "Show selected" view to review the whole selection, and a count of hidden selected items in the selection bar.

## Filtering, as in the FDS

Filtering follows the real Frontend Data Set components (FiltersDropdown, SelectionFilter, DateTimeRangeFilter, ResultsBar):

- **Filter** opens the list of filters, with a search box. Picking one opens its panel with a back arrow.
- **Selection filters** use radios (single) or checkboxes (multiple), an optional autocomplete with the chosen values as removable labels, and an Exclude toggle. Catalog, Product Type and Shippable are the ones Products has in Commerce; Status comes from the CMS.
- **Modified Date** is a From/To range and rejects a "From" after "To".
- The panel button reads **Add Filter**, **Show Results** once an active filter changes, or **Delete Filter** when every value is removed, and stays disabled when there is nothing to apply.
- The results bar shows "N Results Found for:" with a chip for the search and one per filter (first three values plus a +N badge). Clicking a chip edits that filter in place; × removes it. **Clear** resets the search and the filters, never the selection.

Selection changes and result counts are announced to screen readers. On narrow screens the bulk actions collapse to icons and the overflow menu.

The Figma flows live in [LPD-109703 Search while filtering](https://www.figma.com/design/3WtKI99O64OGbcaPqZ2zlr/LPD-109703-Search-while-filtering?node-id=1-2).
