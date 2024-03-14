# Name

Overview

## Description

## Demo

## Features

- feature:1
- feature:2

## Requirement

## Usage

### Download the CodeQL CLI zip package

```shell
curl -LO https://github.com/github/codeql-action/releases/download/codeql-bundle-v2.16.4/codeql-bundle-linux64.tar.gz
tar xvf codeql-bundle-linux64.tar.gz
```

### Check CodeQL Usage

```shell
cd codeql
./codeql -h
```

```shell
Usage: codeql <command> <argument>...
Create and query CodeQL databases, or work with the QL language.

GitHub makes this program freely available for the analysis of open-source software and certain other uses, but it is
not itself free software. Type codeql --license to see the license terms.

      --license              Show the license terms for the CodeQL toolchain.
Common options:
  -h, --help                 Show this help text.
  -v, --verbose              Incrementally increase the number of progress messages printed.
  -q, --quiet                Incrementally decrease the number of progress messages printed.
Some advanced options have been hidden; try --help -v for a fuller view.
Commands:
  query       Compile and execute QL code.
  bqrs        Get information from .bqrs files.
  database    Create, analyze and process CodeQL databases.
  dataset     [Plumbing] Work with raw QL datasets.
  test        Execute QL unit tests.
  resolve     [Deep plumbing] Helper commands to resolve disk locations etc.
  execute     [Deep plumbing] Low-level commands that need special JVM options.
  version     Show the version of the CodeQL toolchain.
  generate    Commands that generate useful output.
  github      Commands useful for interacting with the GitHub API through CodeQL.
  pack        Commands to manage QL packages.
  diagnostic  [Experimental] Create, process, and export diagnostic information.
```

#### `resolve`: [Deep plumbing] Helper commands to resolve disk locations etc.

```shell
./codeql resolve -h
```

```shell
Usage: codeql resolve <command> <argument>...
[Deep plumbing] Helper commands to resolve disk locations etc.
Commands:
  languages           List installed CodeQL extractor packs.
  extractor           [Deep plumbing] Determine the extractor pack to use for a given language.
  qlpacks             Create a list of installed QL packs and their locations.
  queries             [Deep plumbing] Expand query directories and suite specifications.
  library-path        [Deep plumbing] Determine QL library path and dbscheme for a query.
  database            [Deep plumbing] Report metadata about the database.
  upgrades            [Deep plumbing] Determine upgrades to run for a raw dataset.
  qlref               [Deep plumbing] Dereferences a .qlref file to return a .ql one.
  tests               [Deep plumbing] Find QL unit tests in given directories.
  files               [Deep plumbing] Expand a set of file inclusion/exclusion globs.
  ram                 [Deep plumbing] Prepare RAM options.
  metadata            [Deep plumbing] Resolve and return the key-value metadata pairs from a query source file.
  ml-models           [Deprecated] [Deep plumbing] Determine accessible machine learning models.
  extensions          [Deep plumbing] Determine accessible extensions. This includes machine learning models and data
                        extensions.
  extensions-by-pack  [Deep plumbing] Determine accessible extensions for the given paths to pack roots. This includes
                        machine learning models and data extensions.
```

### Create CodeQL Database

```shell
git clone https://github.com/geekcomputers/Python.git 
```

```shell
cd codeql
./codeql database create -l python -s ../Python ../codeqldb
```

### Analyze databases with the CodeQL CLI

```shell
./codeql database analyze ../codeqldb --format csv --output ../result.csv 
```

```shell
Shutting down query evaluator.
Interpreting results.
Analysis produced the following diagnostic data:

|                    Diagnostic                     |       Summary        |
+---------------------------------------------------+----------------------+
| Python extraction warnings                        | 1 result (1 warning) |
| Could not process some files due to syntax errors | 1 result (1 warning) |
| Extracted Python files                            | 628 results          |

Analysis produced the following metric data:

|                         Metric                          | Value |
+---------------------------------------------------------+-------+
| Total lines of user written Python code in the database | 31134 |
```

#### Clone target project

```shell

```

## Installation

## References

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

- github: <https://github.com/shinyay>
- twitter: <https://twitter.com/yanashin18618>
- mastodon: <https://mastodon.social/@yanashin>
