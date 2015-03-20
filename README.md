hubot-plusplus-userverify
==============

Give (or take away) points from people and things, all from the comfort of your
personal Hubot. This is a simple fork off of the popular hubot-plusplus hubot-script.
The changes made, although somewhat hacky, are in place to attempt to clean up
goofy scorings while running the script in Slack with a team. Changes are noted
below.

User Validation Works like so, the bot will take the last word of a multi word 
message and check to see if it matches a username or is the prefix of a username.
If so, it will give the score to that username and drop the first part of the
message. 

For instance, the message `other words go here USERNAME++`, would give USERNAME
an extra point. However, the message `other words++` would give `other words` an
extra point unless a user is in the room that has `words` as part of their username.

All other commands work as designed in hubot-plusplus.

Official Hubot-plusplus repo is located here: https://github.com/hubot-scripts/hubot-plusplus

API
---

* `thing++` - add a point to `thing`
* `(misc message text) thing++` - add a point to `thing`
* `++` - add a point to the most previously voted-on thing
* `thing++ for stuff` - keep track of why you gave thing points
* `thing--` - remove a point from `thing`
* `--` - remove a point from the most previously voted-on thing
* `thing-- for stuff` - keep track of why you removed thing points
* `hubot erase thing` - erase thing from scoreboard (permanently deletes thing from memory)
* `hubot erase thing for reason` erase given reason from thing's score board (does not deduct from total score)
* `hubot top 10` - show the top 10, with a graph of points
* `hubot score thing` - check the score for and reasons for `thing`

Uses Hubot brain. Also exposes the following events, should you wish to hook
into it to do things like print out funny gifs for point streaks:

```coffeescript
robot.emit "plus-one", {
  name: 'Jack'
  direction: '++' # (or --)
  room: 'chatRoomAlpha'
  reason: 'being awesome'
}
```

## Installation

Run the following command 

    $ npm install hubot-plusplus-userverify

Then to make sure the dependencies are installed:

    $ npm install

To enable the script, add a `hubot-plusplus-userverify` entry to the `external-scripts.json`
file (you may need to create this file).

    ["hubot-plusplus-userverify"]
