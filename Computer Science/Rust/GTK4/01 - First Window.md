
```Rust
use gtk::prelude::*;
use gtk::{Application, ApplicationWindow, Button, glib};

const APP_ID: &str = "org.gtk_rs.HelloWorld";

fn main() -> glib::ExitCode {
    // Create a new application
    let app = Application::builder().application_id(APP_ID).build();

    // Connect to "activate" signal of `app`
    app.connect_activate(build_ui);

    // Run the application
    app.run()
}

fn build_ui(app: &Application) {
    // Create a button with label and margins
    let button = Button::builder()
        .label("Press me!")
        .margin_top(12)
        .margin_bottom(12)
        .margin_start(12)
        .margin_end(12)
        .build();

    // Connect to "clicked" signal of `button`
    button.connect_clicked(|button| {
        button.set_label("Hello World!");
    });

    // Create a window
    let window = ApplicationWindow::builder()
        .application(app)
        .title("My GTK App")
        .child(&button) // attach button
        .build();

    window.present();
}
```

- `{rust} use gtk::prelude::*;` imports useful traits for widgets, signals and other methods
- `{rust} use gtk::{Application, ApplicationWindow, glib};`
	- `{rust} Application` provides the [application](https://gtk-rs.org/gtk4-rs/stable/latest/docs/gtk4/struct.Application.html) builder  using [builder design pattern](https://rust-unofficial.github.io/patterns/patterns/creational/builder.html), handles GTK initialization, application uniqueness, session management etc.
	- `{rust} const APP_ID: &str = "org.gtk_rs.HelloWorld";` creates a unique application ID
	- `{rust} let app = Application::builder().application_id(APP_ID).build();`