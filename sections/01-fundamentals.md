# NodeCG fundamentals

## architecture
- nodecg hosts 1 webserver
- nodecg hosts 1 dashboard
- nodecg hosts 0..n replicants
- nodecg hosts 0..n bundles
- bundles host 0..n graphics and panels
- bundles host 0..1 extensions
- graphics, panels, extensions consume NodeCG API

## bundles
A unit of user code.

## the dashboard (and its panels)
This is the web user interface of NodeCG.
Bundles have control panels.
The panels show up on the dashboard.
Each panel is a web page.

## graphics
Graphics go on stream.
They are a web page with a transparent background.
They are displayed by a Browser Source in the streaming software.

## extensions
Extensions are server code from bundles.
Usually this is code that must keep running for a while.
Maybe a connection to twitch chat?
Maybe an interface to a chess AI.

## replicants
Clever code-machines to share data around NodeCG.
If we put text in them from the dashboard, then that text is in the graphic!
And next time we run NodeCG it will load that text from disk.
But replicants can do so much more.
