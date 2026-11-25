# TokenSaver

Orchestrator for the TokenSaver repos. Each TokenSaver.* folder is a git submodule; clone with `git clone --recurse-submodules`.

`TokenSaver.slnx` contains every project across the submodules. Projects reference each other through published AiDevTools.* NuGet packages, so restore needs the AiDevHelpers GitHub Packages feed.
