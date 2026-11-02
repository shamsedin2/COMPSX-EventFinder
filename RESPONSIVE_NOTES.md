# Responsive Design Notes – Events Page

## Problems found in DevTools (before)

**375px (mobile)**
- The sidebar stayed a fixed 280px wide and sat next to the grid instead of stacking.
- The grid was still 2 columns, so the cards were squeezed off the right side of the screen. The page said "Showing 20 events" but no cards were visible.
- The page needed horizontal scrolling.
- 40px page padding and the 42px heading took up too much space on a small screen.
- The header logo (32px) and 40px nav gap didn't fit on one line.
- The "View Details" button was about 36px tall, which is below the 44px minimum touch target.

**768px (tablet)**
- The 280px sidebar plus 40px gap left too little room for 2 card columns, so cards were cramped and titles wrapped badly.

**1024px (desktop)**
- Worked, but everything used fixed pixel values, so nothing scaled.

## Fixes

- Converted pixel values to `rem` units in `EventsList.css`, `EventCard.css` and `Header.css`.
- Mobile-first base styles: sidebar and grid stack in one column, both full width. The grid uses flexbox with one card per row.
- Tablet breakpoint (`min-width: 48rem` / 768px): 2 cards per row using `flex-basis: calc(50% - gap/2)`. The sidebar stays stacked on top so the cards get the full width.
- Desktop breakpoint (`min-width: 64rem` / 1024px): sidebar (17.5rem / 280px) sits beside the grid, and the grid takes the remaining space with `flex: 1`.
- Event card: the image uses `aspect-ratio: 16 / 9` with `object-fit: cover`, so it never stretches. Titles wrap, and the "View Details" button is at least 2.75rem (44px) tall. It's full width on mobile.
- Header: smaller logo and nav gap on mobile, and nav links have 44px touch targets.
