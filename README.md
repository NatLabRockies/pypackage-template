# Template for NLR's Python packages

This is an opinionated template for creating Python packages at NLR,
intended for a wide range of users. If you are new to NLR or don't have
much experience building Python packages, this template is a good option
to provide you a scaffolding to get started quickly. It also sets up several
support tools for you, such as automated checks on your code, automatic
documentation generation, and tests validation on every pull request.
If you're an experienced Python developer, you still have some control by
answering a few questions during the initialization process, which helps avoid
a plain copy and paste from your other projects. We use this
template ourselves.

## Quickstart

### 1) Install Copier

This template is based on [Copier](https://copier.readthedocs.io), a tool to
copy files and directories from a template repository to a destination
directory, while allowing you to answer questions to customize the
destination. You can install `copier` in several ways, depending on your
environment and preferences. Here are some common methods, please choose one
that suits you best:

#### Homebrew (OSX)

If you are on OSX and have [Homebrew](https://brew.sh/), you can install
`copier` globally with the following command:

```bash
brew install copier
```

#### Pixi (contributors)

Install [Pixi](https://pixi.sh/latest/#installation) and:

- Clone this repository and activate it's environment:

  ```bash
  git clone https://github.com/NatLabRockies/pypackage-template.git
  cd pypackage-template
  pixi shell
  ```

- Or create your own environment:

  ```bash
  pixi init my_project_creator
  pixi add copier
  pixi shell
  ```

We use pixi for development. If you would like to contribute to this repository or want to build your own template, we strongly recommend using Pixi.

#### uv

If you prefer using [uv](https://docs.astral.sh/uv/#tool-management), you can install `copier` with the following command:

```bash
uv tool install copier
```

Note: If you use `poetry`, you might want to consider moving to `uv`.

#### pipx

If you have [pipx](https://pypa.github.io/pipx/) installed, you can install `copier` with the following command:

```bash
pipx install copier
```

#### Nix flake

If you are using [Nix flakes](https://nixos.wiki/wiki/Flakes), you can install `copier` with the following command:

```bash
nix profile install 'https://flakehub.com/f/copier-org/copier/*.tar.gz'
```

### 2) Build your package

```bash
copier copy https://github.com/NatLabRockies/pypackage-template ../my_new_project
cd ../my_new_project
```

You should see several files and directories created from the information
that you gave.

If you've made changes to the template repository and would like to test them out locally,
you can do so by adding `--vcs-ref HEAD` to the `copy` command:

```bash
copier copy --vcs-ref HEAD ./pypackage-template ../my_new_project
cd ../my_new_project
```

### 3) Test your build

Once your project structure has been built, you can make sure everything works as intended
by running the tests:

```bash
pixi run tests
```

If this command succeeds, your repository has successfully been set up from the template.

### 4) Add more dependencies

Now you are ready to continue to customize your repository!
For instance, take a look at the `pyproject.toml` file.
Your package will probably depend on other libraries. Let's assume that
you'll use `xarray`, so you can run

```bash
pixi add xarray
```

which will update the `pyproject.toml` and `pixi.lock` files with the new
dependency.

If you want to add more tools for development that do not impact the library dependencies,
you can set the feature flag like this:

```bash
pixi add --feature dev jupyter
```

This will add ``jupyter`` as a package that is available for anyone working in the ``dev``
environment without requiring it as a dependency for all installs of your package.
