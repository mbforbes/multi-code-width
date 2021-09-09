# multi-code-width

Can we automatically generate multiple code widths for reading code on mobile?

For JS/TS:
- [x] Disable automatic syntax highlighting by Jekyll's markdown parser
- [x] Grab blocks
- [x] Run formatter and replace
- [x] Run highlighter
- [ ] Multiple widths
- [ ] Select appropriate width on-the-fly
- [ ] Get jsdoc prettier plugin running
- [ ] Modify jsdoc prettier plugin to also format `//` comments

Nice-to-have:
- [ ] Make everything as non-blocking as possible

## Brainstorming

Doing things client-side (i.e., on the webpage; as in current draft) has the limitation that we can only support languages that have formatters written in JavaScript. While WASM is a thing---and, admittedly, I haven't tried it---I have doubts that setting up a buncha different environments and software for every language we want wouldn't be a huge pain.

Doing things at build-time (server-side) could go a few different ways. Having a universal interface to a code formatter (e.g., [Unibeautify](https://unibeautify.com/)) would be ideal---though I'm not super confident about how easy to use that library is, or whether there are others. This would also mean substantially more configuration than just dropping a script in a webpage.

- We could keep code inside fenced blocks in markdown files and run as a Jekyll (Ruby) plugin or custom config code. Since GitHub doesn't support any custom Jekyll plugins, we'd have to abandon using GitHub's Jekyll build. This wouldn't be terrible---would just need to build the site before pushing and have GitHub host the raw static files. Not that excited about hooking things up with Ruby, though.

- We could keep code inside fenced blocks, then make a tool to insert the different formatted versions and JavaScript switching code below the blocks at build / before-push time. This would then muck up the markdown files, unless what was inserted were include directives.

- We could abandon the fenced blocks, and just do an include which inserts the files. Then, the include could insert the multiple width versions, and code to switch between them. This would potentially decouple the generation of multiple widths from how they're inserted in the page. But having code blocks inside the markdown itself is really nice for authoring content.
