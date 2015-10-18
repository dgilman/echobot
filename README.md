# echobot - synchronize chat rooms

echobot is a simple python3 asyncio bot to echo conversations from one chatroom or network to another.  It currently supports echoing between Hipchat and IRC networks but can be easily extended to new networks and is greatly configurable.

## Setup

Requires [slixmpp](https://slixmpp.readthedocs.org/) for HipChat and [irc3](https://github.com/gawel/irc3) for irc support.  slixmpp has its own dependencies, some in C, so be sure to double-check those dependencies are properly installed.

Install the echobot from pip

    pip install echobot

You need to configure the bot with Python.  There's an [example config file in the repo](https://github.com/dgilman/echobot/blob/master/config.py.example).  Put this somewhere, fill it out and make it executable.

To run the bot, just run your configuration file - it'll start the server processes up.

## Extending the bot

Configuration is simple - write a class whose init takes a function broadcast_msg and implements an async (coroutine) function send_msg.  Do whatever you want in your class - set up the bot, connect, get on the event loop - and when you have a message to echo to the other connections, pass it to broadcast_msg().  The send_msg() you implement will be called when other bots have a message that is to be echoed by you.

I've broken out formatting functions in the bot class so you can implement them in the config class if you want custom formatters.
