# Introduction 
This is an example of a re-useable hybrid-repo, SharePoint (SPFx) MVC implementation. It uses git-modules, yarn workspaces, PNPjs, Spfx-Controls, MobX and Fluent UI.
The goal is to provide a starting point for rapid SPFX development.

## Summary
The example workspaces share the same SharePoint Controller and Spfx views. 
It hopefully illustrates:
- git modules to organise reusable extendable projects (hybrid repro)
- reusable modules for the basics, data source access and presentation
- create a model for the SharePoint access
- focus on business logic development
- an extendable framework by YOUR contribution

# Table of contents
1. [Getting Started](#getting-started)
    1. [Minimal path to awesomeness](#minimal-path-to-awesomeness)
    5. [Create new project](#create-new-project)
2. [Overview](#overview)
    1. [Hybrid repo](#hybrid-repo)
    2. [Shared dependencies](#shared-dependencies)
    3. [Work on modules and app simultanteously](#work-on-modules-and-app-simultanteously)
    4. [Shared modules](#shared-modules)
    5. [MobX for state management](#mobx-for-state-management)
3. [How to use it](#how-to-use-it)
    1. [Process](#process)
    2. [Work on shared modules](#work-on-shared-modules)
4. [Contribute](#contribute)
    1. [Quick start](#quick-start)
    2. [To do list](#to-do-list)

# Getting Started
## Minimal path to awesomeness
Go to any of the example in the `solutions` folder and follow the `README.md`.

### Alternatively to get it all in one go
```
yarn global add lerna
git clone --recurse-submodules https://github.com/mauriora/reusable-hybrid-repo-mvc-spfx-examples.git
```
then go into any subfolder in the `solutions` folder:
- follow the instructions in `README.md`
- **except the `yarn global add lerna` and the `git clone`**

## Create new project
To jump start a new SPFx project, use any of the examples in the `solutions` folder as a starting point:
- Fork the example workspace as *YOUR-SOLUTION*
- Clone the forked workspace
- Fork the starting app project as *YOUR-PROJECT*
- Add *YOUR-PROJECT* as submodule to *YOUR-SOLUTION*
    - the app GitExtenson can be helpfull
    - under `Repository`/`Manage submodules...`
- Remove the starting project, and any other you don't need, from *YOUR-SOLUTION* *(see previous step)*
- call `yarn initguids` in apps/*YOUR-PROJECT*
- rename *YOUR-.....* in:
    - app/*YOUR-PROJECT*
        - package.json
        - src/webparts/*YOUR-WEBPART*
            - *YOUR-WEBPART*.manifest.json
        - config
            - config.json
            - package-solution.json

# Overview
The goal of this project is to provide a starting point, to rapidly develop components while re-using and enhancing shared libraries.

The `README.md` in the submodules document the specific component, like Controller. This document focuses on the shared architecture and shared processes.

## Hybrid repo
Each workspace appears like a mono-repo on the local hard drive, yet it's created from independent repositories.

## Shared dependencies
Using yarn workspace mostly one `node_modules` folder is shared between all projects within a workspace.

## Work on modules and app simultanteously
You can enhance a shared module and use/test it immediately in your app without publishing it.

## Shared modules
Each of the workspaces uses (some) shared modules.

### Controller-SharePoint-List
The MV**Controller** implementation and (currently) contains the base classes of the **Model**VC).

### Utils-SPFx-Controls-React
The M-**View**-C providing wrappers and tools for @pnp/SPFX-Controls-react and @FluentUI/react. 
Mostly being HOCs providing an uniform interface to work with the MVController.

## MobX for state management
MobX is used for state management and data-driven events. Instead of creating and registering specific events, the observer pattern is used.

# How to use it
This explains how to use the different aspecpts of the MVC implementation and hybrid-repos.

## Process
1. Create the workspace (fork & clone) with all required modules
2. Create models for your lists
3. Implement your business logic

## Work on shared modules
When updating code in a shared module, run `yarn build` in the module and the changes are available in the workspace.
Usually you would have an app running using `serve`, go to any of the app files and save it (without modifying), this
will cause webpack to reload your changes in a shared module.

## Models
Models often live in a shared module, as you may use the same model in different workspaces and solutions.

# Contribute
Any contribution is valued and helps.

## Quick start
Please submit your pull request to the corresponding repositories development branch.

## To do list

### Documentation
1. [ ] Architecture overview

### Framkework
1. [ ] [Create new project](#create-new-project) process
1. [ ] Replace lerna with
    2. [ ] yarn    
    1. [ ] rushstack
2. Create build pipelines
    1. [ ] .sppkg
    2. sub modules npm packages
        1. [ ] Azure
        2. [ ] NPM

### Implementation
1. [ ] Styling (js based)
2. Controller
    1. [ ] Single Column Taxonomy fix through TaxCatchAll field

### Modules
1. [ ] Utils module
2. [ ] Config module (e.g. default tsconfig, eslintrc, ...)
3. [ ] Theming/branding module per client


