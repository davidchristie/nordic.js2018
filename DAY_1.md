# Day 1

## Building Foundations of the Node.js Community

Speaker: Tierney Cyren

Slides: https://www.slideshare.net/TierneyCoren/building-foundations-of-the-nodejs-community-nordicjs-2018

http://openopensource.org

`nodejs/community-committee` - A top level committee, sitting next to the Technical Steering Committee and Board

`nodejs/i18n` - The Node.js internationalization Working Group

`nodejs/user-feedback` - User Feeback Initiative

`nodejs/outreach` - diversity, inclusivity, and outreach

`nodejs/website-redesign` - Facilitating the redesign of the nodejs.org website

How to get involved:
- go to `nodejs/community-committee`
- search for issues labelled `good first issue`

## Fast but not furious: debugging user interaction performance issues

Speaker: Anna Migas

Slides: https://www.slideshare.net/AnnaMigas1/nordicjs-fast-but-not-furious-debugging-user-interaction-performance-issues

Debugging user performance interactions

Perceived performance - smooth at all times

60 fps

New devices need 120 fps

Offload the main thread
- Web Workers for heavy tasks

What creates layers?
1. 3D or perspective transforms
2. Animated 2D transforms or opacity
3. Being on top of compositing layers

`will-change` CSS property

Every layer consumes memory, use them wisely

Avoid animating height, width etc

Also avoid animating color, background-color

Animate transform, opacity as it's handled by GPU

Performance tab in DevTools record interactions (short recordings are easier to debug)

Layers tab (Chrome) - information about each layer

Rendering tab
- layer borders
- paint flashing
- FPS meter

There are browser differences in what triggers repaints

Performance monitor tab (Chrome)

Potentially dangerous UI patterns
- Animations
  - don't overuse
  - animate only transform and opacity
  - avoid requestAnimationFrame for 120 fps
  - don't animate elements below other nodes (like fixed headers)
  - don't animate too many elements at once

- Parallax effect
  - triggers repaint every frame
  - almost always bad

- Fixed elements
  - repaints with every scroll
  - use `will-change` property

- Scrolling events
  - don't attach wheel or touch listeners to the whole document, use smaller areas instead.
  - take advantage of passive event listeners (use with pollyfill)

## WebAssembly as cross-platform architecture?!

Speaker: Benedek Gagyi

Slides: http://beng-nordic.surge.sh/#/

[AssemblyScript](https://github.com/AssemblyScript/assemblyscript) - TypeScript that compiles to WebAssembly

## Magic Tricks with Houdini

Speaker: Sam Richard

Slides: http://snugug.github.io/magic-tricks-with-houdini/#/0/0

http://houdini.glitch.me/

Low level API for browser rendering engine

Can pollyfill CSS features in JavaScript

Not ready yet

Typed OM

Custom CSS properties

`window.CSS.registerProperty`

Paint API

Animation API (under active development)
- takes animation off the main thread

Layout API (under active development)
- make your own `display` properties

## Lightning talk

Speaker: Krzysztof Żuraw

TypeScript makes refactoring much easier
- can use `tsc --noEmit` to check everything compiles without generating output
- run `tsc --noEmit` in watch mode during refactoring
- `Code References` - how many times a function is used

## Lightning talk

Speaker: Alexander Karlsson

`picasso.js` data visualisation library - built on d3, uses component layers

https://picassojs.com/

## Can you tell me if your Node app is healthy?

Speaker: Alejandro Oviedo García

Slides: https://slides.com/a0viedo/can-you-tell-if-your-node-app-is-healthy#/

Event loop allows async code execution

If event loop is busy, incoming HTTP connections may be left unattended

Open source ways of getting event loop metrics?
- Prometheous + Grafana
  - can graph event loop lag but doesn't seem to match the actual lag

- `nodejs-dashboard` - gives accurate graph of event loop lag

Why was Prometheous incorrect?
- it polls at regular intervals, too infrequent to see spikes

InfluxDB

Prometheous can be removed as a dependency

fastify -> `under-pressure`
express -> `restify`
hapi -> built in support

## Manage your styles as it's 2018

Speaker: Katarzyna Jastrzębska-Łachacz

Styling in React
- plain CSS - not component-centric
- plain CSS & BEM (naming conventions) - cannot be enforced on developers
- inline styling - don't do this, breaks cascades
- CSS modules - good but not perfect, harder to make components reusable
- CSS-in-JS - pretty good

CSS -in -JS
- Aphroditie (framework agnositic)
- Fela (generates atomic CSS - keeps bundle size small, framework agnostic)
- Emotion(still in development, framework agnostic)
- Styled-components

All support:
- browser prefixes
- SSR
- React-Native

All have roughly the same performance

## Corrections and Constructive Criticism

Speaker: Tessa Kelly

Slides: https://slides.com/tessak/nordic-js#/

## Building a Design System in React

Speaker: Dominic McPhee

https://polaris.shopify.com/

React + TypeScript

Documentation written in markdown

Design tokens - constant style properties

Components have restrictive API by design, makes it easier to update design in future

Many types are shared across components

Comments in code used to automatically generate component documention

Each component has a README that is the source of truth for usage and guidelines

Shopify use SASS and CSS modules

They use a tool to generate CSS namespaced by component name so consumers can use it without React

Use Context API to remain agnostic in state management
- can pass`linkComponent` in context to supply library specific link component

It's open source
- people can vote on issues

Adding new components
- fork existing components

Components focus on solving specific problems

Deprecate unused components

## Lightning talk

Speaker: Lucas Reis

Slides: https://nordicjs-finite-state-machines.netlify.com/#0

How to plan in Agile?
- finite state machines
- statecharts
- xstate

## Lightning talk

Speaker: John Leidegren

content as a first-class citizen
- data driven
- compiler infrastructure - TypeScript
- hacks TypeScript compiler to add data annotations

## Look mum, no hands!

Speaker: Charlie Gerard

Mind control with JavaScript

Explore alternative interactions
- wearables
- voice
- motion
- facial recognition
- biofeedback

Emotiv Epoc - neural biofeedback

How does the brain work?
- different parts of the brain have different functions
- cerebellum is responsible for motor functions

10-20 system EEG - where electrodes are attached

Emotiv Epoc - has simpler electrode placement

`epoc.js` - get data from Emotiv Epoc in JavaScript

EmoComposer emulator

Access to live data
- has built in gyroscrope, accelerometer
- performance metrics
- facial expressions
- 10 trainable mental commends(push, drop, lift, left, right, etc)

Live demos
- brain keyboard - use facial expressions to navigate keyboard
- navigating 3D environment
- controlling a drone

Limits
- the commands need to be trained for each user
- can't track everything, some commands are easier to train than others
- latency, due to live data being feed into machine learning modules
- temporal vs spatial resolution - Emotiv Epoc is best a temporal resolution, MRI have great spatial resolution

Opportunities
- accessiblity
- mential health
- art "creating useless stuff", "useless is not worthless"

Next
- OpenBCI - open source brain sensor
- image reconstruction - reconstruct images that a person is seeing

Getting started
- cheap brain sensors
- other bio sensing tools

## Powerful Automation with the Chrome DevTools Protocol

Speaker: Trent Willis

Slides: https://noti.st/trentmwillis/wls5J4/powerful-automation-with-the-chrome-devtools-protocol#smxp5Su

You can inspect the DevTools inspector
- that means it has a JavaScript API, this is called the DevTools Protocol

[Puppeteer](https://github.com/GoogleChrome/puppeteer) - high level API for Chrome DevTools Protocol

`npm install puppeteer`
`npm install qunit` (or whatever test framework)

Why puppeteer instead of Selenium or Cypress ?
- more flexiable

Visual regression testing
- `npm install looks-same`

`npm install jest` - snapshot testing for entire application
- `expect(await page.content()).toMatchSnapshot()`

Memory leak detection
- by heap
  - check to see if heap increases during interaction
  - probably not a good idea, depends on browser implementation details
- by prototype
  - can query the browser to confirm that all objects with specified prototype have been removed

User Flow Code Coverage
- puppeteer coverage API
- `puppeteer-to-instanbul` to generate coverage reports

Multi-User (browser) End-To-End Testing

Check A11y

RESTful APIs

Web scrapping

Automating webbased workflows
- e.g. Screenshot Emailer
- record + playback service, AKA reproduction service

`puppeteer-recorder` - Chrome extension to generate puppeteer scripts

Chaos UI Testing
