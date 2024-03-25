# todo-indicator

An Ubuntu app indicator for [todo.txt](http://todotxt.org/)-style todo lists.

![todo-indicator indicating](https://raw.github.com/keithfancher/todo-indicator/master/todo-indicator-shot.png)


## Installation

Install `todo-indicator` with `pip`:

```bash
pip install todo-indicator
```

However, **todo-indicator has some system dependencies which `pip` can't
satisfy**. The following should ensure you have everything you need:

```bash
sudo apt install python3-pyinotify python3-gi gir1.2-appindicator3-0.1
```

(The above is verified working on Ubuntu 20.04 and 22.04. I can't speak for
other versions or distros, but it will likely be something similar.)

You can also simply clone the repo and run the provided `todo-indicator`
binary directly, without installing it. You'll still need to install the
required dependencies as described above, however.


## Requirements

* Python 3
* The above-mentioned system dependencies
* An app-indicator-aware system tray of some kind (you might need a plugin if
  you're running a non-Ubuntu distro)


## Usage

Just run `todo-indicator`, passing the name of your `todo.txt` file as an
argument, e.g.:

```bash
todo-indicator ~/todo.txt
```

Click the indicator icon to see your list. If you finish one of your tasks,
give yourself a pat on the back and click it! It'll be marked "done."


### Editing your list

`todo-indicator`'s goal is to show you your list and let you check items off.
Anything more complex than that, you'll want to use your trusty text editor.

Click "Edit todo.txt" and your todo list will open in your text editor of
choice. (Or your OS's text editor of choice, at least -- it uses `xdg-open`.)
Once you've made your changes and saved the file, you should see your updates
automatically reflected in the `todo-indicator` UI. (Thanks, `inotify`!)

If for some reason the indicator doesn't update, click "Refresh".


### Command-line options

Use `-e`/`--editor` to specify a text editor other than your default:

```bash
todo-indicator -e gvim ~/todo.txt
```

`todo-indicator` assumes a dark-colored panel by default. If you use a
light-colored panel, you can pass the `-i`/`--invert` option to invert the
icon color:

```bash
todo-indicator -i ~/todo.txt
```
