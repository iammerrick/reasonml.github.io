---
title: Global Installation
order: 10
---

**Before setting up the editor plugins**, you need to install the global binaries needed by them.

### (Recommended) Through Npm/Yarn

| Platform  | Install command
|-----------|-------------------------------------------------------------------------------------------------
| **OSX**     | `npm install -g https://github.com/reasonml/reason-cli/archive/beta-v-1.13.7-bin-darwin.tar.gz`
| **Linux**   | `npm install -g https://github.com/reasonml/reason-cli/archive/beta-v-1.13.7-bin-linux.tar.gz`
| **Windows** | Please see https://github.com/reasonml/reasonml.github.io/issues/195

### (Alternative) Through OPAM

[OPAM](https://opam.ocaml.org) is the native package manager for OCaml. If you come from OCaml and don't have npm/yarn, you can optionally install this way, but be careful!

**If you're on Windows**, please see https://github.com/reasonml/reasonml.github.io/issues/195.

```
opam update
opam switch 4.02.3 # mandatory!
opam install reason.1.13.7
opam install merlin.2.5.4
```

### Troubleshooting

#### Bad Installation

If your installation fail, it might be because you're on npm 5.4.0 (`npm --version`). There was a known bug in npm that's fixed in 5.4.2. Upgrade `npm` and things should work.

If _that_ fails, try https://github.com/reasonml/reasonml.github.io/pull/157. If that succeeds, please upvote that issue. We aren't sure it's the adequate fix in the meantime.

Finally, if things still don't work, please file an issue at https://github.com/reasonml/reason-cli/issues. Sorry for the trouble.

#### Editor Plugin Not Working

- **If you're on Windows**, the current editor tooling support for Windows is shaky. Please help us improve it in https://github.com/reasonml/reasonml.github.io/issues/195. Thank you!

- Make sure you restart your editor. Some of them might not pick up your new shell environment (which now includes the newly installed binaries) without one.

- Try the following:
  ```
  which ocamlmerlin refmt ocamlmerlin-reason
  ```
  It should spit out three paths that contain the word `reason-cli` if the `reason-cli` installation succeeded.

- Check the Merlin version:
  ```
  ocamlmerlin -version
  ```

  It should say "The Merlin toolkit version 2.5.x, for Ocaml 4.02.3". Not OCaml 4.03, not 4.04, etc.

#### Editor Error Message: Unbound Module `Js`, Etc.

If you're on Visual Studio Code, make sure you open the editor at the project's root (where `package.json` and `bsconfig.json` are). You can do so, for example, by invoking `code .` in the terminal at the root.
