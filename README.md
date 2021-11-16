# Tact public beta community site

(note: this repo is private until we start our public beta. Everything else still applies.)

Welcome to Tact community site! Tact source code is not public, but many other parts of our operations are. This repo gives you access to our bug tracker and discussions area.

To report any bugs you find in the Tact closed beta, [create a new issue][new].

## FAQ

See [FAQ](FAQ.md) for common questions and answers.

## Instructions

[Logging.](Logging.md) Tact produces logs through its activity. See this file for info about how to access these logs.

## Clearing local data on macOS

It may be that you get your Tact into a state that keeps crashing on launch. You can reset the client into a state where it starts from zero. You should do two things for this while the client is not running.

### Clear user defaults

Run this command in Terminal: `defaults delete eu.delta8.CChat`

### Remove local data

Open the folder `~/Library/Containers` and remove any folders with "Tact" in their name.

After you do these two things and restart the client, it re-initializes local state and re-downloads recent data. You can get older data by clicking "Load more" in each chat.

[new]: https://github.com/tact/public/issues/new/choose
