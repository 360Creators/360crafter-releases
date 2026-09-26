# Changelog

## 0.1.23

### Each mask shape cuts or keeps (improved)

A mask used to be a list of shapes that were all taken away, with one invert
flag for the whole hotspot. Every shape now carries its own direction: **Cut**
takes its area away, **Keep** fills it back in, and the shapes apply down the
list — so a Keep traced inside a Cut brings the hotspot back through that gap.

- Switch a shape between Cut and Keep in the mask list; the order in the list is
  the order they are applied, so a Keep has to sit below the Cut it reopens
- Lets one hotspot show through a doorway inside an area that is otherwise
  masked out, which previously needed the shapes traced the other way round
- Masks saved before this open unchanged, and the short-lived whole-mask invert
  flag is cleared the next time the hotspot is saved

### Fixes

- Opening a project that uses a custom HTML hotspot preset no longer sends the
  whole properties panel into the error screen. The preset's style scope was
  looked up as if it were one of the builtin ones, which threw on every mount.
- The error screen is no longer a dead end: alongside **Refresh Page** it now
  offers **Back to Dashboard** and **Contact Support**.

## 0.1.22

### Cut people and objects out of a hotspot with Masks

A panorama is a flat photograph, so a video or a box laid onto a wall paints
over anything standing in front of it — a person, a pillar, a kiosk. The new
**Mask** section in the style panel answers that: trace what should cover the
hotspot and that shape is punched out of it, so the panorama behind shows
through and the objects in the photo read as being in front again.

- Press **+** and click around the object; click the first point again or press
  Enter to close the shape, Esc to stop drawing, Backspace to take a point back
- Click a shape to reshape it: drag a point, drag a midpoint to add one,
  Alt-click to remove one, Backspace to delete the whole shape
- Each corner rounds on its own — drag the handle beside a point, or use the
  slider — so a shoulder can be soft while the floor line stays sharp
- Works on video hotspots, HTML hotspots and polygons; several shapes can be
  traced on one hotspot and each gets its own colour in the list
- The shape is stored on the surface itself, so it keeps its place when the
  hotspot is moved, resized, tilted or fitted to new corners, and travels to
  every linked placement with the rest of the style
- **Done** leaves masking, **Clear mask** removes every shape

### Style a linked hotspot per panorama

A hotspot linked across several panoramas shares one style, so changing its
colour changed it everywhere. It now has two style chips: **All linked · N**,
which edits every placement the way it always did, and **This panorama**, which
stores overrides on the placement you have selected.

- Overrides are drawn over the shared style in the editor, the viewer and the
  export, so one panorama can carry its own colour, size or position
- The chip's × resets that panorama back to the shared style
- Resize handles follow whichever chip is selected
- Bulk edits, saves and newly created placements all keep each panorama's own
  overrides instead of copying one placement's style over the rest

### Group and sort the panorama list

The panorama list in the scene hierarchy gets a **Sort by** menu next to the
existing Group by, so a long tour can be put in the order you want to read it
in rather than the order it was imported.

- Sort by the panorama's name or by any CMS field
- Click the active field again to flip between ascending and descending
- The choice is remembered, so the list opens the way you left it
- Dragging to reorder is paused while a sort or grouping is on, since a drop
  position says nothing about the stored order

### Repeat a hotspot's background image (improved)

A hotspot's background image always tiled sideways, which printed the same
picture several times across a plain uploaded image. There is now a **Repeat**
setting — No repeat, Horizontal, Vertical or Both — with a default that suits
the source.

- A linked panorama's thumbnail still tiles horizontally, which is what lets the
  degrees-based Offset scroll the image past the hotspot's edges
- A plain uploaded image defaults to no repeat, so it is drawn once
- Hover, active and visited states each take their own Repeat

### The editor says why an action did not happen

Some actions are refused rather than failed, and until now nothing said so. A
small hint now appears right where you clicked, explaining the block and, where
there is one, offering the shortcut that clears it.

- Deleting a hotspot that follows a panorama filter used to look like it worked,
  then the hotspot came back the next time the link was reconciled. The delete
  is now refused with a hint, and the hint's button opens **Link to Panoramas**
  at the filter you have to remove first
- Works for one hotspot or a whole selection, with the hint naming how many
- Resizing while a mask is being drawn is blocked, and the hint points at the
  **Done** button in the Mask section
- **Unlink** on a selection breaks the link without touching the placements:
  every panorama keeps the hotspot it already has, they just stop following one
  definition

### Fixes

- Callout, Tooltip and Radar now show up on a hotspot when the values come from
  its preset. They used to appear only when the hotspot carried values of its
  own, so a preset-defined callout showed an empty section with a "+".
- Deleting a hotspot's last action no longer silently shadows the actions it
  inherits from its preset — the hotspot goes back to running the preset's
  actions instead of quietly doing nothing.
- A tilt solved by Fit Corners, or written by a drag in the viewer, no longer
  resets itself the next time the hotspot's style is rebuilt by linking it,
  attaching a preset or switching the editing scope.
- Clearing a polygon's tooltip text puts the Tooltip section back on offer,
  rather than leaving an empty one behind.

## 0.1.21

### New skin component: video

![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image.png)

The skin has a new **Video** component, so a clip can sit in a corner of the
frame instead of out in the scene. It is set up exactly like a video hotspot:
paste a URL or upload a file, and the same Chroma Key controls key a greenscreen
presenter out onto the tour behind them.

- Loop, Muted and Autoplay work as they do on a hotspot, with the same defaults
- Key colour, Similarity, Smoothness and Spill are the hotspot's controls, so a
  clip keyed in a panorama looks the same in the skin
- **Pick In Viewer** takes the key colour straight off the clip on the canvas
- Fit chooses whether the clip is letterboxed, cropped or stretched to its box
- **Match clip shape** sizes the box to the clip, so a presenter is neither
  cropped at the edges nor floating in empty space; an uploaded clip shapes its
  box by itself as long as you have not resized it yet

### New action: Play video

![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image-2.png)

Actions have a new **Play Video** entry, so a clip no longer has to autoplay to
ever run. Point it at a video component and pick Play, Pause, Stop or
Play / Pause.

- Point it at a video component in the skin or at a video hotspot in a panorama
- Put it on an icon or a box for a play button, or on the video itself so
  clicking the presenter starts and pauses them
- Hotspots, map pins and 3D models can drive a video too
- A clip you paused stays paused while you move around the tour, instead of
  restarting itself the next time the panorama is drawn
- Play / Pause restarts a clip that has finished, so one button is enough
- Stop rewinds to the first frame

### Drop a hotspot into a screen, wall or doorway with Fit Corners

![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image-3.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image-4.png)
![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image-5.png)

Putting a hotspot flat against something in the panorama used to mean nudging
the rotation on three axes and resizing until it looked right. **Fit Corners**,
in the Transform section, turns the four corner handles into a perspective fit:
drag them onto the corners of a screen, a poster or a doorway and the hotspot's
position, rotation and size are all solved from where you put them.

- The X, Y and Z rotation fields fill themselves in as you drag
- The four corners are the whole shape, so a square hotspot can be fitted to a
  widescreen frame — the aspect ratio lock is ignored while the mode is on
- Works for HTML and video hotspots that are set to Fixed; switching one to
  Floating turns the mode back off, since a floating hotspot faces the camera
- A corner you drag somewhere no flat rectangle could reach simply stops
  following, rather than folding the hotspot away
- One undo takes the whole fit back

### Drag a hotspot anywhere in one go

![](https://360creators.github.io/360crafter-releases/assets/v0.1.21/image-6.png)

Moving a hotspot to the other side of the room used to mean dropping it at the
edge of the viewer, turning the view and picking it up again. Now the view turns
for you: hold the hotspot near an edge and the panorama follows, with the
hotspot staying under your cursor.

- Works at every edge — left and right turn the view, top and bottom tilt it
- The closer you are to the edge, the faster it turns; move back in and it stops
- Groups and polygons can be carried around the same way

## 0.1.20

### Fixes

- 0.1.19 is now available on Mac too — the Mac download was held back by a
  signing problem, now fixed

## 0.1.19

### Faster panorama tiles, without the freeze

Big panoramas used to lock up the whole app while their tiles were generated —
a 20k panorama could leave you staring at a spinning cursor for a very long
time. Tiles are now made in the background, so you can keep working while they
build, and they finish in seconds instead.

- Importing several panoramas at once no longer piles the work up in parallel;
  they're processed one after another
- Exporting a tour with missing tiles no longer fails: the tiles are generated
  first, Background processes opens so you can follow along, and the export
  carries on by itself
- New projects start with **Compatible tiled panoramas** switched on

## 0.1.18

### Presenting 360Crafter updates

Presenting the updates nicely in this new 360Crafter updates window.

- The window now also opens once after an update has installed, so you can read
  what changed in the version you just got — not only before you download it

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
