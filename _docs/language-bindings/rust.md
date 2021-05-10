---
---

# GTK and Rust

## About

[**gtk-rs**](https://gtk-rs.org/) project deals with the Rust bindings for GTK, Cairo and other GLib-compatible libraries.

The bindings of Cairo, Pango, Gio, Graphene, GLib are part of the the [gtk-rs](https://github.com/gtk-rs/gtk-rs/). While the bindings of GTK 4 are part of [gtk4-rs](https://github.com/gtk-rs/gtk4-rs/)

## gtk-rs Documentation

There is an official [gtk4-rs API Documentation](https://gtk-rs.org/gtk4-rs/git/docs/) for using GTK and Rust together.

There are also a growing number of examples and thorough tests of language features in the test suite.

You can see all the gtk-rs examples [here](https://github.com/gtk-rs/gtk4-rs/tree/master/examples).

## A Hello World app

```rust
use glib::clone;
// glib and other dependencies are re-exported from the gtk crate
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
    // Create a new application
    let app = gtk::Application::new(Some("com.github.gtk-rs.examples.basic"), Default::default());
    app.connect_activate(on_activate);
    // Run the application
    app.run();
}
```

### Explanation

This code depicts how to use GTK Rust binding for creating a simple Hello World application.

## Tutorials

[**gtk-rs**](https://gtk-rs.org/) website lists various [tutorials](https://gtk-rs.org/docs-src/tutorial/) that range from introduction to the usage of Gtk-rs crates and much more. An introduction to building GUI application with Rust and GTK 4 is also available in the form of a [book](https://gtk-rs.org/gtk4-rs/git/book/). If you want more tutorials please refer to the [FAQ](https://gtk-rs.org/docs-src/faq) page on the gtk-rs website.

## Contribute

If you are interested in contributing to the gtk-rs binding project, you can get a head start by reading the instructions on how to get started for contributing to gtk-rs [here](https://github.com/gtk-rs/gtk4-rs#contribute).

If you want to get in touch with the original source files, you can visit the project's [git repository](https://github.com/gtk-rs/gtk4-rs) on GitHub.

## See More

* Project: [https://github.com/gtk-rs/gtk4-rs](https://github.com/gtk-rs/gtk4-rs)
* Docs: [https://gtk-rs.org/gtk4-rs/git/docs/](https://gtk-rs.org/gtk4-rs/git/docs/)
* Book: [https://gtk-rs.org/gtk4-rs/git/book/](https://gtk-rs.org/gtk4-rs/git/book/)
