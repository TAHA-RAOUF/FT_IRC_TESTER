# Black Wolf ft_irc Tester

Terminal tester for the 42 `ft_irc` project.

It can:

- show a Black Wolf ASCII intro
- launch your `ircserv` binary automatically
- connect to an already running server
- run `normal`, `bonus`, or `global` test suites
- open a raw IRC command terminal for manual testing

## Quick Start

Put the tester beside your `ircserv` binary, then run:

```sh
python3 scripts/test_irc.py
```

The default command expects:

- binary: `./ircserv`
- host: `127.0.0.1`
- port: `6667`
- password: `mypass`

## Common Commands

Run mandatory tests:

```sh
python3 scripts/test_irc.py --mode normal --binary ./ircserv --port 6667 --password mypass
```

Run bonus tests:

```sh
python3 scripts/test_irc.py --mode bonus --binary ./ircserv --port 6667 --password mypass
```

Run the full global tester:

```sh
python3 scripts/test_irc.py --mode global --binary ./ircserv --port 6667 --password mypass
```

Test a server that is already running:

```sh
python3 scripts/test_irc.py --no-start --host 127.0.0.1 --port 6667 --password mypass --mode global
```

Open a raw IRC terminal:

```sh
python3 scripts/test_irc.py --mode terminal --no-start --host 127.0.0.1 --port 6667 --password mypass
```

Inside the terminal, type IRC commands like:

```irc
JOIN #test
PRIVMSG #test :hello
MODE #test +i
TOPIC #test :new topic
```

Use `/quit` to leave the tester terminal.

## Bonus Bot Test

If your bonus includes a bot, pass its nick:

```sh
python3 scripts/test_irc.py --mode bonus --bot-nick mybot
```

The tester sends `!help` to the bot and checks for a `PRIVMSG` or `NOTICE`
reply.

## Environment Variables

You can configure defaults with:

```sh
export IRC_TEST_HOST=127.0.0.1
export IRC_TEST_PORT=6667
export IRC_TEST_PASSWORD=mypass
export IRC_TEST_BINARY=./ircserv
export IRC_TEST_TIMEOUT=4
export IRC_TEST_BOT_NICK=mybot
```

Then run:

```sh
python3 scripts/test_irc.py --mode global
```
