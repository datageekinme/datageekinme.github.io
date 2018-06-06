---
title: "Ranges"
permalink: /mastering-python/notes-0002/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Notes #3: `range` and `xrange`"
---

## Ranges: `range` and `xrange`:

### `range`:
The `range` type represents an immutable sequence of numbers and is commonly used for looping a specific number of times in `for` loops.

**Syntax:**
```python
range(stop)
range(start, stop[, step])
```
`step` argument defaults to 1. Can be negative or positive.

`range` returns a `list` object

### `xrange`:

Similar to `range` i.e. generates a sequence of numbers. `xrange` does not actually generate a static list at run-time like range does. Creates the values as needed with a techinque called `yielding`. This techinque is used with a type of object called `generators`.

`xrange` returns a `xrange` object

NOTE: `xrange` does not exist in Python 3. `range` does what `xrange` used to do in Python 2. {: .notice--warning}

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
