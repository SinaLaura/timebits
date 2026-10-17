# Timebits

A minimal countdown and Pomodoro timer for your phone or browser. Set the minutes, press Start, and watch time pass one small item at a time.

Tap an item and it reacts. Tap the empty background and the whole look changes. Pause whenever you need a break; the time waits for you.

**Try it:** https://sinalaura.github.io/timebits/

It is a web app that can be installed to the home screen (PWA) and works offline. It is plain HTML and JavaScript, with no build step and no external dependencies.

## Run it locally

```
cd docs
py -m http.server 8765
```

Then open http://localhost:8765. Handy for trying things out:

- `?m=10` starts a 10 minute countdown right away
- `&look=<name>` picks a specific look

## Project layout

```
docs/       the app (also what GitHub Pages publishes)
lab/        experiments, not part of the app
resources/  app icon source
```

## Roadmap

Packaging the app for the app stores with [Capacitor](https://capacitorjs.com).
