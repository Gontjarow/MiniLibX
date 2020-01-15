### How to register an event with MLX?

An "event" is some kind of function being called (or triggered) by some action.

For example, clicking your mouse would cause an event. If there is no function (or handler) registered for the mouse event, nothing will happen. So, how would you do something when a mouse is clicked?

From the [loop_hook manual page](mlx_loop_hook), we know that `mlx_mouse_hook` can be used to register an event handler for the mouse, and we know how the event handler will be called.
```
int mouse_event(int button, int x, int y, void *param)
{
    // Whenever the event is triggered, print the value of button to console.
    ft_putnbr(button);
}
```

It's important to note that your event handlers should be registered before `mlx_hook` because that function will never return. You can register new handlers and replace old ones after `mlx_loop` has started, as long as you have at least one handler active so your program can respond to actions.
```
int main()
{
    void *mlx = mlx_init();
    void *win = mlx_new_window(mlx, 640, 360, "Tutorial Window - Draw Pixel");

    mlx_mouse_hook(win, &mouse_event, 0);

    mlx_loop(mlx);
}
```
