### Synopsis
```
int mlx_pixel_put(void *mlx_ptr, void *win_ptr, int x, int y, int color);

int mlx_string_put(void *mlx_ptr, void *win_ptr, int x, int y, int color, char *string);
```

### Description
The `mlx_pixel_put` function draws a defined pixel in the window `win_ptr` using the (`x`,`y`) coordinates, and the specified color.

The origin (`0`,`0`) is the upper left corner of the window, the X and Y axis respectively pointing right and down.

The connection identifier, `mlx_ptr`, is needed (see the [mlx man page](mlx.md)).

Parameters for `mlx_string_put` have the same meaning. Instead of a simple pixel, the specified string will be displayed at (`x`,`y`).

In both functions, it is impossible to display anything outside the specified window, nor display in another window in front of the selected one.

### Color Management
The color parameter has an integer type. The displayed color needs to be encoded in this integer, following a defined scheme.

All displayable colors can be split in 3 basic colors: red, green, and blue. Three associated values, in the 0-255 range, represent how much of each color is mixed up to create the original color. These three values must be set inside the integer to display the right color.

The three least significant bytes of this integer are filled as shown in the picture below:
```
| 0 | R | G | B | color integer
+---+---+---+---+
```

While filling the integer, make sure you avoid endian problems. Remember that the "blue" byte should always be the least significant one.

### Additional notes (not in the manual)
The fourth value mentioned in color management is the alpha (transparency) value. This is also in the 0-255 range, where 0 is fully opaque (visible) and 255 is fully transparent (invisible).

MacOSX (for example) uses little-endian, meaning that the least significant byte is the first in memory. This means that if you are writing things into memory (such as [images](mlx_new_image.md)) byte by byte, you'll have to write them in this format:
```
| B | G | R | A | Blue, Green, Red, Alpha
+---+---+---+---+
```

### Author
Copyright ol@ - 2002-2015 - Olivier Crouzet

Re-format and spelling corrections by Gontjarow

Additional notes by Gontjarow
