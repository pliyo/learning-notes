# Building new facebook v2

[link](https://www.youtube.com/watch?v=KT3XKDBZW7M&list=PLPxbbTqCLbGHPxZpw4xj_Wwg8-fdNxJRh&index=40)

#

- `Big challenges`: How to decrease time to visually complete?

  - `Traditionally`:
    - 1st JavaScript.
    - 2nd Render while we fetch data.
    - 3rd Render again.
  - `Now`:
    - Relay handles all the data fetching for us.
    - As soon as server receives the request it can inmediately render the page, so we can load the content earlier.
    - html flushing + incrementaly sending the markup. Flush incomplete markup almost immediately.
    - Start with the markup that it's faster to generate, such as metatags. We can flush this almost almost immediately.
    - Once the client starts to download the JavaScript and CSS much ealier in the page load, in paralel while the server is still generating the HTML. Meanwhile the server moves to page and user specific resources.
    - Start putting a UI skeleton of how the UI will look like.
    - `Code splitting` divide the first skeleton into pieces, dynamic imports aren't quite right, it's better to use Lazy loading without waiting for any code execution to happen. Wait to different between things we want later or at the beginning.
      With dynamic import when resources will be needed.
    - Two new declaratives APIs:
      - `importForDisplay()` puts everything bellow it in phase 2.
      - `importAfterDisplay()` pushes everything below it in the phase 3.
      - We have 3 phases at build time (Phase 1: Loading, Phase 2: Display, Phase 3: Analytics).
    - It phase will render exactly what we expect.
    - Ensure we are only sending resources that we actually need, at build time strip things that don´t belong for this user.
    - `Suspense boundaries` work like a try catch. First try to render the context, then uses a loading

- `Html flushing`: When a browser request an HTML document it receives the response in pieces in the form of network packages. As it receives it, incrementaly parses the HTML, this happens even before the entire document has been downloaded.
- `Time to first paint`: How long it takes us to put the first round of pixels in the screen.
- `Time to first meaningful paint`: How long it takes for the first meaningful content to be visible.
- `Relay new feature`: Ability to mark which part of our query can be streamed down, so we can wait for the rest. We can mark which information is less urgent.
- `Suspense` is react system for orchestrating the loading of code, data and images. Suspense let us wait for something before rendering.
