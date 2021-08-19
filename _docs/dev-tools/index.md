---
---

# Using GTK

To compile a GTK application, you need to tell the compiler where to find
the GTK header files and libraries. This is done with the
[`pkg-config`](https://www.freedesktop.org/wiki/Software/pkg-config/)
utility.

The following interactive shell session demonstrates how `pkg-config` is used
(the actual output on your system may be different):

```sh
$ pkg-config --cflags gtk4
-I/usr/include/gtk-4.0
-I/usr/include/pango-1.0
-I/usr/include
-I/usr/include/glib-2.0
-I/usr/lib64/glib-2.0/include
-I/usr/include/harfbuzz
-I/usr/include/freetype2
-I/usr/include/libpng16
-I/usr/include/libmount
-I/usr/include/blkid
-I/usr/include/fribidi
-I/usr/include/libxml2
-I/usr/include/cairo
-I/usr/include/pixman-1
-I/usr/include/gdk-pixbuf-2.0
-I/usr/include/graphene-1.0
-I/usr/lib64/graphene-1.0/include
-mfpmath=sse -msse -msse2
-I/usr/include/gio-unix-2.0
-pthread
$ pkg-config --libs gtk4
-lgtk-4
-lpangocairo-1.0
-lpango-1.0
-lharfbuzz
-lgdk_pixbuf-2.0
-lcairo-gobject
-lcairo
-lgraphene-1.0
-lgio-2.0
-lgobject-2.0
-lglib-2.0
```

The simplest way to compile a program is to use the "backticks" feature of
the shell. If you enclose a command in backticks (not single quotes), then
its output will be substituted into the command line before execution. So to
compile a GTK "Hello, World" application, you would type the following:

```sh
$ cc `pkg-config --cflags gtk4` hello.c -o hello `pkg-config --libs gtk4`
```

# Development environments

You can use various integrated development environments to write your GTK
applications, as well as contributing to GTK.
