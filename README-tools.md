# Demo SvelteKit: tools

For some of our projects, we create helper tools, such as typical shell scripts.

Our naming convention is to put these tools here:

```sh
mkdir bin
```


### markdown-reader-to-headline

File <bin/markdown-reader-to-headline>:

```sh
grep -m1 '^##*[[:space:]][[:space:]]*[^[:space:]]' "$@" |
sed 's/^#*[[:space:]]*//; s/[[:space:]]*#*[[:space:]]*$//;'
```


### clean

For some of our projects, we create a helper tool that we name `clean`.

The tool aims to reset the project to its original state.

For example, the code below deletes all normal routes, yet does not affect any special routes that start with a plus character.

File <bin/clean>:

```sh
#!/bin/sh
set -euf
find .src/routes -type f ! -name '+*' -exec rm {} \;
```

This tool enables us to quickly clean up routes.

Example before:

```
src/routes/+layout.svelte
src/routes/+page.svelte
src/routes/alfa.bravo
src/routes/charlie.delta
```

Example after:

```
src/routes/+layout.svelte
src/routes/+page.svelte
```


### slugs

For some of our projects, we create a helper tool that we name `slugs`.

For example, the code below searches a pre-existing git repository, that contains a directory named `topics`, that contains pre-existing subdirectories, that each contain a markdown content file named `index.md`. The tool parses the directories into web-friendly slugs.

File <bin/slugs>:

```sh
GIT_TOP_DIR="$(git rev-parse --show-toplevel)"
DIR="$GIT_TOP_DIR/topics"
find "$DIR" -name 'index.md' -type f -exec dirname {} \; |
sort | cut -c $(( ${#DIR} + 2 ))-
```

Example input pre-existing directory structure:

```txt
my-project/topics/alpha/index.md
my-project/topics/bravo/index.md
```

Example output slugs:

```txt
alpha
bravo
```
