### How to use the "param" for event handlers in MLX?

Only one pointer sure seems cheap. You can't even use `mlx_pixel_put` with that!

Let's modify a [previous tutorial](mlx-tutorial-draw-pixel.md) where we drew a pixel in the middle of the window, and combine it with the [other tutorial](mlx-tutorial-register-event-handlers.md) about event handlers. This time we'll draw the same pixel only after a mouse button is pressed.

```
int mouse_event(int button, int x, int y, void *param)
{
    // Soon...
}

int main()
{
    void *mlx = mlx_init();
    void *win = mlx_new_window(mlx, 640, 360, "Event Parameters");

    mlx_mouse_hook(win, &mouse_event, 0);

    mlx_loop(mlx);
}
```

It's about time you learned the importance of structs. Let's define a simple structure for our whole program.
```
typedef struct  s_program
{
    void *mlx;
    void *win;
}               t_program;
```

We can use this to hold both pointers grouped together and easily accessible. The value of `void *mlx` is copied into `tutorial.mlx` so that they both point to the same address in memory.
```
int main()
{
    void *mlx = mlx_init();
    void *win = mlx_new_window(mlx, 640, 360, "Event Parameters");

    t_program tutorial;
    tutorial.mlx = mlx;
    tutorial.win = win;

    mlx_mouse_hook(win, &mouse_event, &tutorial);

    mlx_loop(mlx);
}
```

Now, when `mouse_event` is called, you can typecast `param` to a type you know it will be. `t_program` in this case.
```
int mouse_event(int button, int x, int y, void *param)
{
    t_program *tutorial = param;
    mlx_pixel_put(tutorial->mlx, tutorial->win, 640/2, 360/2, 0xFFFFFF);
    return (1);
}
```
WIP
