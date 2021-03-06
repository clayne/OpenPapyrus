# Open Papyrus Project

## Overview

The Open Papyrus Project (OPP) provides open source grammars that describe the 
Papyrus language. This language is used by Bethesda Softworks and authors of
mods for games such as *The Elder Scrolls V: Skyrim* and *Fallout 4*.

This project's intent is to facilitate the development of language tools &mdash;
such as syntax highlighting, inspections, refactorings, code clone analysis, and
build automation &mdash; by producing accurate and efficient grammars.

## Project Status

Currently, this project consists of only the lexer and parser grammars for
Papyrus scripts and the flags file.

These grammars were ported from the ANTLR3 .NET implementations to ANTLR4
grammars. They are based on the implementations for *Fallout 4*, which is
assumed to implicitly describe Papyrus for *Skyrim*.

Work has not yet started on the following grammars:

- Papyrus Type Walker
- Papyrus Release and Final Processor
- Papyrus Optimizer
- Papyrus Var Cleaner
- Papyrus Code Generator

The available grammars have not been fully tested.

### How are these grammars used by the compiler?

The compiler makes use of each grammar in the following order:

1. Loads and parses scripts into objects (`PapyrusParser`)
2. Creates a dictionary of parsed flags (`FlagsParser`)
3. Checks for type safety (`PapyrusTypeWalker`)
4. Performs release and final processing (`PapyrusReleaseProcessor`)
5. Optimizes expressions (`PapyrusOptimizer`)
6. Cleans up temporary and unused variables (`PapyrusVarCleaner`)
7. Builds final tree and formats data with string template (`PapyrusGen`)

The compiler then passes control to the assembler which writes `.pex` output.

## Contributing

Grammar contributions and testing are appreciated. Here's how to get started:

1. Install [PyCharm](https://www.jetbrains.com/pycharm/). A free Community Edition is available.
2. Install the [ANTLR v4](https://plugins.jetbrains.com/plugin/7358-antlr-v4) and [StringTemplate v4](https://plugins.jetbrains.com/plugin/8041-stringtemplate-v4) plugins.
3. Use the ANTLR Preview tool to test and profile rules.

For developers, submit pull requests. For everyone else, submit issues.

## Legal Notice

The Open Papyrus Project is not affiliated, endorsed, or authorized by ZeniMax
Media, Bethesda Softworks, or Microsoft in any way.
