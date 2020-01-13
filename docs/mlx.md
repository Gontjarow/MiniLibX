### Synopsis
```
#include <mlx.h>

void *mlx_init();
```
### Description
MiniLibX is an easy way to create graphical software, without any X-Window/Cocoa programming knowledge. It provides simple window creation, a drawing tool, image and basic events management.

### Include File
`mlx.h` should be included for a correct use of the MiniLibX API. It only contains function prototypes, no structs are needed.

### Library Functions
First of all, you need to initialize the connection between your software and the display. Once this connection is established, you'll be able to use other MiniLibX functions to send the graphical orders, like "I want to draw a yellow pixel in this window" or "did the user hit a key?".

The `mlx_init` function will create this connection. No parameters are needed, and it will return a `void *` identifier, used for further calls to the library routines.

All other MiniLibX functions are described in the following man pages:

- [mlx_new_window](mlx_new_window.md)   -- Manage windows
- [mlx_pixel_put](mlx_pixel_put.md)     -- Draw inside windows
- [mlx_new_image](mlx_new_image.md)     -- Manipulate images
- [mlx_loop](mlx_loop.md)               -- Handle keyboard or mouse events

### Return Values
If `mlx_init` fails to set up the connection to the graphical system, it will return `NULL`, otherwise a non-null pointer is returned as a connection identifier.

### BSD/Linux X-Window Concept
X-Window is a network-oriented graphical system for Unix.

It is based on two main parts:
- On one side, your software wants to draw something on the screen and/or get keyboard & mouse entries.
- On the other side, the X-Server manages the screen, keyboard and mouse (It is often refered to as a "display").

A network connection must be established between these two entities to send drawing orders (from the software to the X-Server), and keyboard/mouse events (from the X-Server to the software).

### MacOSX Concept
The MacOSX operating system handles graphical access to the screen (or "display").
- On one side, your software wants to draw something on the screen and/or get keyboard & mouse entries.
- On the other side, the underlying MacOSX graphical framework that handles the screen, the windowing system, keyboard and mouse.

A connection between these two entities must be established.

### Author
Copyright ol@ - 2002-2015 - Olivier Crouzet

Re-format and spelling corrections by Gontjarow
