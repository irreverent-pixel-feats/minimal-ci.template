# minimal.template

## Description

### `TL;DR`

A minimal [ecology](https://github.com/irreverent-pixel-feats/ecology) template that
just intialises a project with a `README.md`.

It also forms the reference implementation for the Ecology template interface.

### More

#### How to Write an Ecology Template

Ecology templates have two main features:

- A `template-files` directory
- A `bin/bootstrap-template` script.

Understanding what to do with each is best done by understanding what Ecology does
to initialise a project:

##### How Ecology Initialises a Repos contents

It reads all the commits from the master branch of the template repository into the master branch of
the new repository.

It then runs `bin/bootstrap-template`, at the moment, it passes it the following environment:

| Environment Variable          | Value |
|-------------------------------+----------------------------------------------------------------|
| `ECOLOGY_PROJECT_NAME`        | The name of the project from the `EcologyProject` declaration  |
| `ECOLOGY_PROJECT_DESCRIPTION` | The short description of the project from the `EcologyProject` declaration |

After the script returns, the `bin/bootstrap-template` script and `template-files` directory are deleted.

It then either keeps the commits from the template, and commits the new state of the repo on top of it,
or it squashes the whole lot into one commit, depending on how you setup your ecology process.

So basically:

For all static content that does not depend on specific project parameters: Just put them in the template
exactly where you would expect them in the projects that spawn from it.

For content that depends on specific project parameters (like the name of the project, for example),
then you create it with the `bin/bootstrap-template` script. You can put any additional files you may
need for this in the `template-files` directory, and know that that directory will be deleted.

See the [`bin/bootstrap-template`](./bin/bootstrap-template) script and [`template-files`](./template-files)
directory in this repo for examples.
