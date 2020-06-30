# chronometrist-goals
Adds support for time goals to [Chronometrist](https://github.com/contrapunctus-1/chronometrist/)

## Installation
You can get `chronometrist-goals` from https://github.com/contrapunctus-1/chronometrist-goals/

`chronometrist-goals` requires [alert.el](https://github.com/jwiegley/alert) and, of course, [Chronometrist](https://github.com/contrapunctus-1/chronometrist/)

## Usage
### Define some goals
First, define some goals in `chronometrist-goals-list`
```elisp
(setq chronometrist-goals-list
      '((60 "Programming")
        (30 "Writing" "Composing")
        (30 "Reading" "Music")))
```
The numbers stand for the minutes you want to set as the goal. Observe that you can have any number of tasks after the goal - which is a way of saying you aim to spend that much time on any one of those tasks.

In the above example, we aim to spend 60 minutes on Programming, 30 minutes on either Writing or Composing, and 30 minutes on either Reading or Music.

Note - this variable may be subsumed into `chronometrist`, at an undefinite point in the future.

### Set up hooks
```elisp
(add-to-list 'chronometrist-after-in-functions 'chronometrist-goals-run-alert-timers)
(add-to-list 'chronometrist-after-out-functions 'chronometrist-goals-stop-alert-timers)
```
And you're all set! Run `chronometrist` again and marvel at your goal times displayed in the buffer. You will now be notified when you're five minutes away from the goal, when you have reached the goal, and when you have exceeded the goal by five minutes.

## Customization
See the Customize groups `chronometrist` for variables intended to be user-customizable.

### Notification style
You may be interested in customizing alert.el too, especially `alert-default-style` - the author uses -
```elisp
(setq alert-default-style 'libnotify)
```

### Notification times
The custom variable `chronometrist-goals-alert-functions` is a list of functions which are run by `chronometrist-goals-run-alert-timers`. Each of these functions starts a timer, which notifies you at a certain time.

You can add or remove functions from this list to customize the times at which you are notified. The functions added to the list by default are tiny (7~9 lines) and (hopefully) easy for an interested user to base their own alert functions on.

## Roadmap/Ideas

## Contributions and contact
Feedback and MRs very welcome. 🙂

Contact the creator and other Emacs users in the Emacs room on the Jabber network - [xmpp:emacs@salas.suchat.org?join](https://conversations.im/j/emacs@salas.suchat.org) ([web chat](https://inverse.chat/#converse/room?jid=emacs@salas.suchat.org))

(For help in getting started with Jabber, [click here](https://xmpp.org/getting-started/))

## License
I dream of a world where all software is liberated - transparent, trustable, and accessible for anyone to use or improve. But I don't want to make demands or threats (e.g. via legal conditions) to get there.

I'd rather make a request - please do everything you can to help that dream come true. Please Unlicense as much software as you can.

chronometrist-goals is released under your choice of [Unlicense](https://unlicense.org/) or the [WTFPL](http://www.wtfpl.net/).

(See files [UNLICENSE](UNLICENSE) and [WTFPL](WTFPL)).

## Thanks
wasamasa, bpalmer, aidalgol, and the rest of #emacs for their tireless help and support
