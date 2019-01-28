# Formatting Git Filter

## Background

Different tools modify code files in different ways. For example, `npm install --save` might modify your `package.json` in a slightly different way than if someone manually edited the file and their code editor ran a linter right before they saved the file.

Linters do a good job of reducing meaningless variations in files. The trick is finding the ideal time for them to run.

A common strategy is to run a linter on a file right before the file is saved. The advantage of this strategy is that the invariant is simple -- files on disk should always be linted. However, the implementation turns out to be tricky -- all programs that modify the file need to know how to lint the file in the exact same way.

One way to solve this is for everyone to agree on a standard linter and/or code style. [Prettier](https://prettier.io/) has been emerging as the de-facto linter, so having all standard tools use the Prettier code style (and potentially read config from `.prettierrc`) could be a possibility in the near future.

It's great that keeping files on disk saved in a consistent format is possible, but it feels like a better separation of concerns for the consumer of the file to do the linting. The consumer could be any of the following:

- The person reading the file is the one who would like to read code in a standard coding style.

- The central Git repository is the place where code should have little variation.

- `git diff` needs to normalize files before comparison, to minimize useless parts of the diff.

## Idea

Based on these use cases, a good time to be running the the linter is right before the file enters the Git system. Git has a system for doing that, called filters. A filter can be added to lint files before commit and before diffing.

The Git website has more info on how this works, and even suggests using the filter to auto-indent code:\
<https://git-scm.com/book/en/v2/Customizing-Git-Git-Attributes>

It seems like setting up a filter is a two-step process (you need to set up the filter, then the hook in `.gitattributes` to run the filter for certain file patterns. It's not completely intuitive. Perhaps someone can make a tool like husky (<https://github.com/typicode/husky>) to make setting up filters easier.

However, once the filter is setup, the advantage is clear: there's no need to set up a linter hook for each kind of tool that can modify files. Git will ensure that all code that enters the system is linted.
