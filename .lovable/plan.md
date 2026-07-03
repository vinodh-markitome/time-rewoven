I found the likely cause: the section currently stacks the 1996 Earth image and the 2026 Earth image on top of each other, then fades the 2026 image in with opacity. During the middle of the scroll, both full globes are visible at once, and because the two generated Earth images are not perfectly identical in framing/lighting, it reads as two Earths.

Plan:

1. Replace the opacity crossfade in `04 — Why time matters`
   - Stop fading two full Earth images over each other.
   - Keep the rotating Earth as one circular visual area.

2. Use a clipped reveal instead of opacity overlap
   - Keep the 1996 image as the base layer.
   - Reveal the 2026 image with a scroll-linked `clip-path`/mask so each part of the globe is only showing one image at a time.
   - This preserves the 1996 → 2026 transformation without ever showing two complete Earth discs.

3. Lock the globe container
   - Add a circular `overflow-hidden` wrapper with a stable aspect ratio.
   - Ensure both Earth images share the exact same inset, scale, transform origin, and rotation.
   - Keep the year counter and radial vignette outside the clipped image stack.

4. Verify the scroll states
   - Check the beginning, middle, and end of the section.
   - Confirm only one Earth silhouette is visible at every scroll position.