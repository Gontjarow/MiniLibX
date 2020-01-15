### Synopsis
```
void  * mlx_new_window(void *mlx_ptr, int size_x, int size_y, char *title);

int     mlx_clear_window(void *mlx_ptr, void *win_ptr);

int     mlx_destroy_window(void *mlx_ptr, void *win_ptr);
```

### Description
The `mlx_new_window` function creates a new window on the screen, using the `size_x` and `size_y` parameters to determine its size, and `title` as the text that should be displayed in the window's title bar.

The `mlx_ptr` parameter is the connection identifier returned by `mlx_init` (see the [mlx man page](mlx.md)).

`mlx_new_window` returns a `void *` window identifier that can be used by other MiniLibX calls.

Note that the MiniLibX can handle an arbitrary number of separate windows.

`mlx_clear_window` and `mlx_destroy_window` respectively clear (in black) and destroy the given window. They both have the same parameters: `mlx_ptr` is the screen connection identifier, and `win_ptr` is a window identifier.

### Return Values
If `mlx_new_window` fails to create a new window (for wathever reason), it will return `NULL`, otherwise a non-null pointer is returned as a window identifier. `mlx_clear_window` and `mlx_destroy_window` right now return nothing.

### Author
Copyright ol@ - 2002-2015 - Olivier Crouzet

Re-format and spelling corrections by Gontjarow
