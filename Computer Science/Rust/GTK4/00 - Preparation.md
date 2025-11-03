- this [tutorial](https://gtk-rs.org/gtk4-rs/stable/latest/book/) is used

Make sure the following packages are installed
```bash
sudo pacman -S gtk4 base-devel
```

Create a new project by using `Rust`s package manager 
```bash
cargo my-gtk-app
cd my-gtk-app
```

Check which version of `GTK4` is installed
```bash
pkg-config --modversion gtk4
```
Output can be
>  4.18.6

Then add by
```bash
cargo add gtk4 --rename gtk --features v4_18
```

Run the application by invoking
```bash
cargo run
```

