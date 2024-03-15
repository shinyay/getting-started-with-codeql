# Getting Started with CodeQL at local

The CodeQL CLI (Command Line Interface) is a tool provided by GitHub that allows you to run CodeQL analysis and execute CodeQL queries from the command line on your local machine or in a CI/CD environment.

Some key things to know about the CodeQL CLI:

1. **Database Creation**: It allows you to create CodeQL databases from your source code. These databases contain data/control flow information and are required to run CodeQL queries.

2. **Query Execution**: You can execute custom CodeQL query files or bundles of queries (query suites) against the created CodeQL databases using the CLI.

3. **Integrate with Build Systems**: The CLI can integrate with various build systems like Make, MSBuild, Gradle etc. to automatically build CodeQL databases during code compilation.

4. **Local Analysis**: Running analysis locally enables faster feedback cycles, offline usage, scaling to large codebases effectively using local compute resources.

5. **Output Formats**: Query results can be output in various formats like CSV, SARIF, or print to console using CLI options.

6. **CI/CD Integration**: The CLI facilitates integrating CodeQL analysis into your CI/CD pipelines and pre-commit hooks for consistent code checking.

7. **Distributed Analysis**: For huge codebases, the analysis work can be distributed across multiple machines using the CLI.

So in essence, the CodeQL CLI brings the powerfulCodeQL semantic code analysis capabilities to developers' local machines and automated workflows via a command line interface. It complements the CodeQL cloud service offering.

## Description

While [CodeQL](https://codeql.github.com/) as a cloud service has its own advantages, the local CLI offers more flexibility, control, and tight integration into developer workflows for efficient code analysis.

- **Early Feedback in Development Workflow**
  - Running CodeQL queries locally allows developers to get feedback on code quality and security issues early in their workflow, before pushing code changes. This enables fixing issues sooner rather than later.
- **Customized Analysis**
  - Using the CodeQL CLI locally gives you full control over the analysis. You can write and run custom queries tailored to your project's needs, coding standards, and security requirements that may not be covered by out-of-the-box queries.
- **Faster Turnaround**
  - Local analysis avoids the overhead of uploading source code and waiting for results from a remote service. The CodeQL CLI provides rapid query execution and iterative analysis capabilities.
- ** Pre-Commit Checks**
  - The local CLI enables integrating CodeQL analysis seamlessly into pre-commit hooks or CI pipelines for consistent code checking before commits/merges.
- **Offline Usage**
  - With the CLI, you can create CodeQL databases and run queries locally without an internet connection after the initial setup, enabling use in air-gapped environments.
- **Scaling to Large Codebases**
  - The CodeQL CLI can handle analyzing large, monolithic codebases efficiently on powerful local machines by leveraging multiple cores/threads and optimizing use of memory/disk.
- **Compliance and Auditing**
  - For regulated industries, using an on-premise analysis tool like the CodeQL CLI can help meet compliance requirements around data privacy, control, and auditing better than a cloud service.
- **Learning and Experimentation**
  - The local CLI provides a great environment for developers to learn CodeQL, experiment with new queries, inspect code properties, and build proficiency through hands-on practice.

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

### `database create`

Create a CodeQL database for a source tree that can be analyzed using one of the CodeQL products.

#### Clone target project

```shell
git clone https://github.com/geekcomputers/Python.git 
```

```shell
cd codeql
./codeql database create -l python -s ../Python ../codeqldb
```

### `database analyze`

Analyze a database, producing meaningful results in the context of the source code.

```shell
./codeql database analyze ../codeqldb --format csv --output ../result.csv 
```

```shell
:
:
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

#### **SARIF** format

- `--format sarif-latest`

```shell
./codeql database analyze ../codeqldb --format sarif-latest --output ../result.sarif 
```

## Installation

## References

- [Use the CodeQL CLI to secure your code](https://docs.github.com/en/code-security/codeql-cli)
  - [Getting started with the CodeQL CLI](https://docs.github.com/en/code-security/codeql-cli/getting-started-with-the-codeql-cli)

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

- github: <https://github.com/shinyay>
- twitter: <https://twitter.com/yanashin18618>
- mastodon: <https://mastodon.social/@yanashin>
