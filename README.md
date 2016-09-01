# git-hooks-js-win
write git hooks in javascript - works in Windows

`git-hooks-ws` is an utility for managing and running project [git hooks](http://git-scm.com/docs/githooks) for [nodejs](http://nodejs.org/) projects.

It has zero dependecies and easy to use.

Just [install git-hooks-win](#install) and it will run your hooks when a hook is called by git.

**This version works in Windows 7.**

## Why do you need git hooks in your project?
Hooks are little scripts you can place in `$GIT_DIR/hooks` directory to trigger action at certain points.

They are very powerful and helpful.

You can do a lot of things with them:

  * Validate commit message contents (for example: must include ticket number)
  * [Validate code](http://jshint.com/) and run tests before commit.
  * [Check codestyle](http://jscs.info/).
  * Spell check the commit message or check it format.
  * and etc.

**Note.** When you use `git-hooks-win`, you should not modify `$GIT_DIR/hooks` directory manually because `git-hooks-win` will do it for you.

## Install
Install `git-hooks-win` in your project.
```bash
npm install git-hooks-win --save-dev
```

To keep things organized, `git-hooks-win` looks for scripts in sub-directories named after the git hook name.
All these sub-directories should be stored in `.githooks` directory in the project root.

Let's create some dummy pre-commit hook.
```bash
mkdir -p .githooks/pre-commit
echo -e '#!/usr/bin/env node' "\nconsole.log('hi!');" > .githooks/pre-commit/hello.js
chmod +x .githooks/pre-commit/hello.js
```

Then just try to commit and see how things are rolling.
```bash
git add .githooks package.json
git commit -m "Add git-hooks-win"
```

See also [hooks examples](examples).

It's worth to mention that our library checks for gitignore rules while executing scripts in .githooks/ directories.

## Related projects
  * Copy and edit of [git-hooks-js](https://github.com/tarmolov/git-hooks-js) project
