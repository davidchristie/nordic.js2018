# Day 2

## Node.js: The Road to Workers

Speaker: Anna Henningsen

How did I get into Node.js core?
- error tracing in `setTimeout`

A Node.js application is:
- one process
- one thread*
- one event loop
- one JS Engine instance
- one Node.js instance

Golden rule of Node.js performance: "don't block the event loop"

Existing solutions
- multiple processes
- cluster API

Drawbacks:
- no shared memory
- communitication over JSON

Worker threads

A Node.js application is:
- one process
- multiple threads
- one event loop
- one JS Engine instance
- one Node.js instance

Implementation idea:
- embed Node.js into inself
- need to rethink global state
- need to clean up resources on exit

Prior attempts to add Workers to Node.js in 2015 stalled due to lack of reviewers

In October 2017, Ayo.js was forked from Node.js - implemented Workers

Porting to Node.js - available in Node 10

The result
- not quite the Web Worker API
- require() works
- almost all Node.js core APIs work (can't change global state from inside workers)

Communitication
- ArrayBuffers
- SharedArrayBuffers and Atomics work
- workerData to pass startup data
- MessagePort, MessageChannel close to the browser

Current status: experimental

Future:
  - passing native handles (sockets)
  - more isolation

## The Matrix is Everywhere: A Primer on Projections in Web Graphics

Speaker: Lauren Budorick


WebGL

4-dimension matrix
`mat4 = require('gl-matrix').mat4`

`mat4.create()` (identity matrix)

The matrix multiplication happens in the shader (in the GPU)

Types of matrix transformation:
- translate
- rotate - rotate a matrix around an angle (in radians)
- scale

Order matters in matrix transformations

"model, view, projection"

model - the objects in a scene
view - the camera or viewer
projection - perspective

Order matters: projection * view * model

http://regl.party/

## Accessible by law! Generating colors with JS and CSS Custom Properties

Speaker: Ingvild Indrebø

In Norway websites must comply with accessiblity guidelines

Web Content Accessiblity Guidelines 2.0 (WCAG)

Video calling company needed to let customers pick colours based on their brand - how to deal with accessiblity issues?

Colour contrast

`npm install color`

HSL colour wheel

rotate 60 degrees from primary colour to get secondary colour

Set colours as CSS Custom Properties

## Why we built another framework

Speaker: Tomas Della Vedova

Couldn't improve performance of server frameworks without major breaking changes

`fast-json-stringify` - 2-3x faster

Why not build framework around it? - [`fastify`](https://github.com/fastify/fastify)

Design goals
- speed
- almost zero overhead - low price for a set of features (analysis with framegraph)
- extensible via plugins
- developer experience
- open open source

Everything is a plugin

## Lightning talk

Speaker: Ian Savchenko

Making a smart watch app in JavaScript
- countdown to Friday evening
- calculates week numbers

## Lightning talk

Speaker: Vilberg Eliasson

## Achieving Secure Software through Redesign

Speaker: Mike Samuel

Slides: https://docs.google.com/presentation/d/1AdVNCppkTAQMGxgUux-swP8nVr8Pc9p_Ldvg2GWFCo8/edit#slide=id.p

Security engineer at Google

Content-Security-Policy
- places restrictions on what an HTML document can do
- can be trivially circumvented using JSONP
- XSS is still the top vector
- 3-8% adoption (Gmail still hasn't fully adopted it)
- maintaining a secure whitelist for complex application is infeasible in practice
- CSP is not enough to solve XSS, can be bypassed, hasn't adapted to client-side frameworks

Need to be closer to the code

https://github.com/WICG/trusted-types

We want to perserve the intent of users/developers even when attackers control some of the inputs

Need to ensure the outputs of the application are trusted types

Secure literal templating - HTML, SQL etc

Continuous Integration
- can be used to drive adoptation of best security practice
- detects code using potentially dangerous APIs and tags oncall security engineer as reviewer
- wrap dangerous APIs with safe abstractions

The module graph matters

## Using TypeScript with Redux Architecture

Speaker: Sandi Barr

Angular + Redux

Actions as event streams

RxJS Observables - tools for working with streams

Use TypeScript enums for action types

Use schematics and `ng` CLI to generate Redux-style boilerplate

selectors - pure functions that map state to view layer data

Works with Redux Devtools

## Lightning talk

Speaker: Erik Hellman

Let's make the WebRTC samples better
- WebRTC team aren't web developers
- samples need some love
- should samples be barebones or written in a framework?

## Lightning talk

Speaker: Pierre Reimertz

SnapCat
- Expo React-Native development

## Empathy Driven Development: Boosting performance by implementing for unfavorable conditions

Speaker: Isabella Silveira de Souza

Slides: https://speakerdeck.com/bellasilveira/empathy-driven-development-boosting-performance-by-implementing-for-unfavorable-conditions

## Headers for Hackers

Speaker: Andrew Betts

## Connecting JavaScript to the Blockchain

Speaker Meng Shang

## The Life of a JavaScript Feature in V8 ft. TypedArrays

Speaker: Peter Marshall
