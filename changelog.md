# Changelog

## 0.1.17

### Compare two panoramas side by side

![Compare panoramas side by side](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-4.png)
![Move divider around](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-5.png)
![Insert it from the skin library "Split Compare"](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-6.png)

Put two views in one box and drag the divider between them to reveal more of
either side. Both panes move together, so turning one turns the other — handy
for before-and-after shots of the same room.

- The divider is styled like any other element in your skin
- Dragging is smooth now: the images no longer flash or reload while you drag
- Panoramas placed inside a skin can finally be dragged around with the mouse

### Interactive Media type: Maps

![](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-7.png)

The separate Maps page is gone. Everything it did is now part of a map you add
to a tour, so you set it up in the same place you use it.

- Search for a place by name and the map flies straight to it
- Set Location can open on one of your own tour maps, keeping its style and
  starting view
- The map pin shows up properly again instead of a broken image

### Auto-linking panoramas navigation hotspots

![](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-8.png)
![Inside panorama settings you can Set North.](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-9.png)

If your panoramas have GPS coordinates, one button creates the links between
them, and another removes them again. Assuming that the north is set correctly on each panorama.
If your panoramas do not have GPS, you can drag them on the map and it will assign the relevant GPS coördinates to them.

- Routes are drawn as dashed lines with arrows showing which way each one runs
- Two-way routes sit side by side so you can see both
- Click a line to remove that one direction

### Rounded corners on polygon hotspots (improved)

![Rounded edges around the polygon (new)](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-10.png)
![Before this update, without rounded edges](https://360creators.github.io/360crafter-releases/assets/v0.1.17/image-11.png)

Polygon hotspots get a Corner radius setting, so a hard-edged outline can be
softened into a rounded one. Corners stay evenly rounded whether they're sharp
or wide, and the points you drew stay where you put them.

### Fixes

- Options you typed into a CMS select field were thrown away if you clicked Save
  without pressing Enter first. They're kept now.
- Moving a shape hotspot left its outline and handles behind until you let go of
  the mouse. They follow along as you drag.
- The loading screen now accepts components dropped inside it, like other
  containers.
- Setting north on a project stored on your own computer no longer fails.
- Map thumbnails stop drifting. A map’s card in the media list used to follow the camera live while you were panning and zooming around. Now it always shows the view you deliberately saved with “Set View”.
- Backup of large projects works now as well which gave an error before "Array buffer allocation".

## 0.1.16

### Rich text editor (improved)

![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/image.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/great-lounge-4.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/image-3.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/image-4.png)

Text hotspots and the text skin component now take rich text instead of a single
styled string. One text component can hold a heading and its description, so
there's no need to stack two components.

- Dynamic titles and descriptions
- Ordered and unordered lists
- Per-heading style overrides
- Turn a link into an action — for example, move the camera to a hotspot from a
  list

### Multi-select fields

![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/multi-select.png)

The editor's `Single Select` field is now a `Select` field, with an option to
allow multiple values. Can also be used inside the Rich text editor (un)ordered lists.

### Text button with icon (improved)

![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/button.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.16/button-library-3-2.png)

An `auto`-width box used to always stretch to `100%`, so text + icon buttons didn't really work.
This text+icon button has also been added to the built-in library.

### CMS List pagination

![53 panoramas divided by 8 means 6 pages with 8 items and the 7th page with 6 items.](https://360creators.github.io/360crafter-releases/assets/v0.1.16/pagination-2.png)

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

## 0.1.15

### Skin component library

![](https://360creators.github.io/360crafter-releases/assets/v0.1.15/image.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.15/image-2.png)

Save any component from the tree to a library and drop it into another skin or
project, instead of rebuilding it each time. Popup is now a built-in component.

### Multi-level menus

![](https://360creators.github.io/360crafter-releases/assets/v0.1.15/image-3.png)

Group a CMS List by a field and the Skin renders it as a nested menu, so a tour
with dozens of panoramas can be navigated by area or floor.

### Callout pin and origin controls (improved)

Callouts can be pinned and given an origin point, so they stay attached where you
want them as the camera moves. Panoramas also get their own CMS tab, and the CMS
grid can be edited in place.

### Fixes

- A custom view was ignored on navigation hotspots using the Fade or None
  transition; the camera now lands where you set it.

## 0.1.14

### Panorama presets

![](https://360creators.github.io/360crafter-releases/assets/v0.1.14/image.png)

Save the settings you use most as a preset and apply them to new panorama in one
step. Such as settings for Indoor panoramas and Outdoor panoramas.

### Hotspot editor controls (improved)

Reworked panorama and transform controls in the hotspot editor, plus tidier
preset controls for hotspots and skins.

### Min and max FOV panoramas

![](https://360creators.github.io/360crafter-releases/assets/v0.1.14/image-2.png)

Panoramas can carry their own minimum and maximum field of view.

## 0.1.13

### Fixes

- On Windows, dragging inside a panorama could start a native image drag instead
  of turning the camera.

## 0.1.12

### CMS grid toolbar

![](https://360creators.github.io/360crafter-releases/assets/v0.1.12/image.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.12/image-2.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.12/image-3.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.12/image-4.png)

Hide, filter, group and sort columns straight from the grid toolbar, with field
type icons and collapsible groups.

### Colour-coded filters and named views

Filters and columns can be colour-coded, and a set of filters, sorting and
visible columns can be saved as a named view to switch between.

### Breakpoints for every property (improved)

Any property can now differ per breakpoint, not just a chosen few.

### Export dialog (improved)

Before exporting, the dialog reviews which data connections need syncing, so a
tour doesn't ship with stale CMS data.

### Fixes

- `Cmd+Z` undo in the CMS grid.
- Custom CMS tables are now included in project backups.

## 0.1.11

### CMS quick-edit in the properties panel

![](https://360creators.github.io/360crafter-releases/assets/v0.1.11/image-2.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.11/image.png)

A hotspot's CMS fields can be edited from its properties panel, without switching
to the CMS.

### Callout reveal animations

Callouts can animate into view instead of appearing instantly.

### Callout rendering (improved)

Sharper callout rendering, and linked CMS fields keep their formatting when shown
in a callout.

## 0.1.9

### Linked hotspots and camera action timeline

![](https://360creators.github.io/360crafter-releases/assets/v0.1.9/image-2.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.9/image.png)

Link hotspots together and sequence camera moves on a timeline, to guide visitors
through a tour rather than leaving every move to them.

### Fixes

- Windows installer created its shortcuts unreliably.
- Mac builds occasionally failed to notarize, which could block an update.

## 0.1.8

### Fixes

- Windows installer shortcut hook.

## 0.1.7

### Fixes

- Mac install reliability.

## 0.1.6

### New action: audio

![](https://360creators.github.io/360crafter-releases/assets/v0.1.6/image.png)

Play, pause and stop audio from any action, so a hotspot or skin button can
control narration or ambient sound.

### Download a file from your assets

![](https://360creators.github.io/360crafter-releases/assets/v0.1.6/image-2.png)

Every asset in the library has a download button, so you can pull the original
file back out of a project.

### Optional desktop shortcut on Windows

The Windows installer now asks whether to create a desktop shortcut.

## 0.1.5

### Fixes

- Outline buttons had a low-contrast hover state.

## 0.1.4

### Fixes

- Fixed a glitchy black stripe shape appearing on tablets and mobile devices
- Fixed overusage of ram

## 0.1.3

### Public Beta Launch (launch)

It's been a while working hard on 360Crafter. Today I can proudly announce that the beta version of 360Crafter is available to download. I'm extremely excited and curious to hear opinions.
