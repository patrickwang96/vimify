## Update

The HendrikPetertje's version doesn't work on my vim. I'm using MacVim on my laptop and Ubuntu 18.04 LTS default vim on my desktop machine. 
The problem is that it uses py3 for the vim script. However, I use plugins like YCM that needs python2. Vim does not allow py2 and py3 to load 
at the same time. 

Therefore, I refactored the code from py3 to py2 to fit into my vim. Whoever encountered my problem can refer to this plugin.

### Installation 
The original way is to use pathogen. However, I'm using Vundle to manage my plugins. 
So, simply add this pline to your .vimrc

```
Plugin 'patrickwang96/vimify'
```

## About

![Vimify](https://github.com/patrickwang96/vimify/blob/master/example.png)

[vimify](https://github.com/Hendrikpetertje/vimify) is a plugin for [Vim](https://github.com/vim/vim) 
origionally inspired by [MuAnsari96](https://github.com/MuAnsari96/vimify).
It provides a simple Spotify integration within Vim to search and play music on
OSX and Linux. This version of vimify uses AppleScript to talk with spotify on
Mac and Dbus on linux. If you managed to open vim and load this plugin, your
system will have the right one installed.

Just make sure you have Spotify installed somewhere and the plugin should work.
You will need to have built vim with Python3 support or load python3 in neovim
for this plugin to work.

Big thanks to [Mattpenney89](https://github.com/mattpenney89) for writing the
linux bits and updating the scripts to python 3

For the search functions you will need to follow the new instructions in the setup
part of this readme. Linux support trough Dbus / some code cleaning is underway,
as well as looking for albums and artist.

## Features and Usage
vimify is designed to interface with a running desktop instance of Spotify. Currently, the following features are supported:

* `:SpPlay` will play the current track
* `:SpPause` will pause the current track
* `:SpPrevious` will move to the previous track
* `:SpNext` will move to the next track
* `:Spotify` or `:SpToggle` will toggle play/pause
* `:SpSearch <query>` will search spotify for 'query' and return the results in a new buffer. While working in the Vimify buffer, the name, artist and album of all pertinent tracks will be displayed. Vimify's behavior in this buffer is described as follows::
    * `<Enter>`: If the cursor is over the name of the track, Spotify will begin playback of that track
    * `<Enter>`: If the cursor is over the name of the artist, Spotify will begin playback of all songs by artist, starting with popular
    * `<Enter>`: If the cursor is over the name of the album, Spotify will begin playback of the entire album
    * `<Space>`: Is bound to `:SpToggle` when working in the Vimify buffer

### update March 2018: Vimify now requires authentication.

1. Create a new spotify application at https://beta.developer.spotify.com/dashboard/applications
2. Grab the Client Id and Client secret of your brand new spotify developer application
3. Go to https://www.base64encode.org/ and paste your client id and secret like `client:secret` (don't forget the colon). Example:

```
afff3bbbdffff7ebclientID452855f9:afff3bbbdffff7secretfdfd452855f9
```

4. Grab the encoded result to your clipboard and paste it in your vimrc like:

```
let g:spotify_token='YOURENCODEDRESULTHERE'
```

* It's bit of an extra step to encode it, but safes code in the plugin, plus you
won't be putting a hard-coded password in your env files (though a bas64 string is easy
to spot and more than easy to reverse!!!!).

And you'll be good to go! Once help tags are generated, you can just run `:help vimify` in vim to see the manual.

