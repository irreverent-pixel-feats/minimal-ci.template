# minimal-ci.template

## Description

### `TL;DR`

Minimal [Ecology](https://github.com/irreverent-pixel-feats/ecology) Template, includes our
standard CI hook scripts

### More

We want to be able to shift between CI services as easily as possible.

So we don't really use a lot of the step/workflow type features that these platforms have,
because they are all subtly different and result in vendor lock in. So we just have a standard
set of "hook" scripts in our repos and use the CI services as "automated script drivers".

That way moving from one to the other is about configuring the project on the new platform and
replacing its in repo config file, and nothing else.

This is the kind of stuff that ecology can either do as part of its sync process, or with
a bespoke haskell script that uses ecology as a library...

Its only 3 main scripts:

| Location           | Use                                |
|--------------------|------------------------------------|
| `bin/ci`           | Master CI builds                   |
| `bin/ci.branches`  | Branch CI builds                   |
| `bin/ci.common`    | Local Dev build for entire project |

Naturally, depending on the project, some are subsets of others, so sometimes, they call
each other...
