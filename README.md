# chronometrist-goal
Adds support for time goals to [Chronometrist](https://github.com/contrapunctus-1/chronometrist/)

## Installation
You can get `chronometrist-goal` from https://github.com/contrapunctus-1/chronometrist-goal/

`chronometrist-goal` requires [alert.el](https://github.com/jwiegley/alert) and, of course, [Chronometrist](https://github.com/contrapunctus-1/chronometrist/)

## Usage
First, hook `chronometrist-goal` to `chronometrist` -
```elisp
(add-hook 'chronometrist-mode-hook 'chronometrist-goal-minor-mode)
```

Then, define some goals in `chronometrist-goal-list`
```elisp
(setq chronometrist-goal-list
      '((60 "Programming")
        (30 "Writing" "Composing")
        (30 "Reading" "Music")))
```
The numbers stand for the minutes you want to set as the goal.

Observe that you can have any number of tasks after the goal - which is a way of saying you aim to spend that much time on any *one* of the tasks that follow. In the above example, we aim to spend 60 minutes on Programming, 30 minutes on either Writing or Composing, and 30 minutes on either Reading or Music.

Note - this variable may be subsumed into `chronometrist`, at an undefinite point in the future.

And you're all set! Run `chronometrist` again and marvel at your goal times displayed in the buffer.

With the default configuration, when you start tracking time, you will be notified when you
* are five minutes away from the goal,
* have reached the goal, and
* have exceeded the goal by five minutes.

If a task doesn't have a goal, you will be reminded of the time you have spent on it, every fiften minutes.

## Customization
See the Customize groups `chronometrist` for variables intended to be user-customizable.

### Notification style
You may be interested in customizing alert.el too, especially `alert-default-style` - the author uses -
```elisp
(setq alert-default-style 'libnotify)
```

### Notification times
The custom variable `chronometrist-goal-alert-functions` is a list of functions which are run by `chronometrist-goal-run-alert-timers`. Each of these functions starts a timer, which notifies you at a certain time.

You can add or remove functions from this list to customize the times at which you are notified. The functions added to the list by default are tiny (7~9 lines) and (hopefully) easy for an interested user to base their own alert functions on.

### More
A user desiring even greater control may define their own versions of `chronometrist-goals-run-alert-timers` and `chronometrist-goals-stop-alert-timers` (preferably using them as a template) and add them to the desired hooks.

## Roadmap/Ideas
* clear notifications on file change event
* define types for custom variables
* clock in -> go over the goal, get the 'exceeding' -> clock out, file changes, the exceed alert is shown again

## Contributions and contact
Feedback and MRs very welcome. 🙂

If you have tried using chronometrist/chronometrist-goal, I'd love to hear your experiences! Get in touch with the author and other Emacs users in the Emacs channel on the Jabber network - [xmpp:emacs@salas.suchat.org?join](https://conversations.im/j/emacs@salas.suchat.org) ([web chat](https://inverse.chat/#converse/room?jid=emacs@salas.suchat.org))

(For help in getting started with Jabber, [click here](https://xmpp.org/getting-started/))

## License
I dream of a world where all software is liberated - transparent, trustable, and accessible for anyone to use or improve. But I don't want to make demands or threats (e.g. via legal conditions) to get there.

I'd rather make a request - please do everything you can to help that dream come true. Please Unlicense as much software as you can.

chronometrist-goal is released under your choice of [Unlicense](https://unlicense.org/) or the [WTFPL](http://www.wtfpl.net/).

(See files [UNLICENSE](UNLICENSE) and [WTFPL](WTFPL)).

## Thanks
wasamasa, bpalmer, aidalgol, and the rest of #emacs for their tireless help and support
