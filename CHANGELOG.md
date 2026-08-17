# Changelog

## 0.1.16

### Rich text editor (improved)

![](https://raw.githubusercontent.com/360Creators/360crafter-releases/changelog/changelog/assets/v0.1.16/great-lounge-4.png)

Text hotspots and the text skin component now take rich text instead of a single
styled string. One text component can hold a heading and its description, so
there's no need to stack two components.

- Dynamic titles and descriptions
- Ordered and unordered lists
- Per-heading style overrides
- Turn a link into an action — for example, move the camera to a hotspot from a
  list

### Multi-select fields

![](https://raw.githubusercontent.com/360Creators/360crafter-releases/changelog/changelog/assets/v0.1.16/multi-select.png)

The editor's `Single Select` field is now a `Select` field, with an option to
allow multiple values. Can also be used inside the Rich text editor (un)ordered lists.

### Create buttons (improved)

![](https://raw.githubusercontent.com/360Creators/360crafter-releases/changelog/changelog/assets/v0.1.16/button.png)
![](https://raw.githubusercontent.com/360Creators/360crafter-releases/changelog/changelog/assets/v0.1.16/button-library-3-2.png)

An `auto`-width box used to always stretch to `100%`, so text + icon buttons didn't really work.
This text+icon button has also been added to the built-in library.

### CMS List pagination

![53 panoramas divided by 8 means 6 pages with 8 items and the 7th page with 6 items.](https://raw.githubusercontent.com/360Creators/360crafter-releases/changelog/changelog/assets/v0.1.16/pagination-2.png)

Loading all items at once may reduce loading speed. With pagination you split up the total amount by a number of your choice and it will show you options to see the next or previous sub-list.

### Fixes

- Column auto-flow grids collapsed their first item into a zero-width `1fr`
  track, drawing item 1 underneath item 2. Implicit columns are now sized
  correctly.
- "Navigate to current CMS item" failed on a Box template because the click
  handler received an unbound component. Row data is now carried at every
  nesting depth.
- CMS field selectors resolve through the full ancestor chain, so an image nested
  inside a box inside a CMS List still shows its bindings.
- Deleting a craftspace no longer immediately recreates a default one.
