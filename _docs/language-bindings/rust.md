---
---

# GTK and Rust

## About

The [**gtk-rs**](https://gtk-rs.org/) project contains Rust bindings for GTK, Cairo and other GLib-compatible libraries.

The bindings of Cairo, Pango, Gio, Graphene and GLib are part of [gtk-rs core](https://github.com/gtk-rs/gtk-rs-core/).
The bindings of GTK 4 can be found at [gtk4-rs](https://github.com/gtk-rs/gtk4-rs/).

## gtk-rs Documentation

`gtk4-rs` provides extensive [documentation](https://gtk-rs.org/gtk4-rs/stable/latest/docs/gtk4/index.html) for its API based on GObject-Introspection.
An introduction to building GUI applications with Rust and GTK 4 is also available in the form of a [book](https://gtk-rs.org/gtk4-rs/git/book/).

The gtk4-rs Github repository features additional [examples](https://github.com/gtk-rs/gtk4-rs/tree/master/examples) which demonstrate solutions to specific problems.


## A Hello World app

This code shows how to use `gtk4-rs` to create a simple Hello World application.

```rust
use glib::clone;
// glib and other dependencies are re-exported by the gtk crate
use gtk::glib;
use gtk::prelude::*;

// When the application is launched…
fn on_activate(application: &gtk::Application) {
    // … create a new window …
    let window = gtk::ApplicationWindow::new(application);
    // … with a button in it …
    let button = gtk::Button::with_label("Hello World!");
    // … which closes the window when clicked
    button.connect_clicked(clone!(@weak window => move |_| window.close()));
    window.set_child(Some(&button));
    window.present();
}

fn main() {
    // Create a new application with the builder pattern
    let app = gtk::Application::builder()
        .application_id("com.github.gtk-rs.examples.basic")
        .build();
    app.connect_activate(on_activate);
    // Run the application
    app.run();
}
```

## See More

* Project: [https://github.com/gtk-rs/gtk4-rs](https://github.com/gtk-rs/gtk4-rs)
* Docs: [https://gtk-rs.org/gtk4-rs/git/docs/](https://gtk-rs.org/gtk4-rs/git/docs/)
* Book: [https://gtk-rs.org/gtk4-rs/git/book/](https://gtk-rs.org/gtk4-rs/git/book/)
