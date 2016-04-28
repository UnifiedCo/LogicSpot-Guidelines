# LogicSpot GIT Workflow

## Table of Contents

 1. [Support Workflow](#support-workflow)
    - [Support Rules](#support-rules)
    - [Support Diagram](#support-workflow-diagram)
 1. [Project Workflow](#project-workflow)
    - [Project Rules](#project-rules)
    
## Support Workflow

### Support Rules

 1. Work MUST be branched off of **master**
 1. Feature branches MUST be prefixed with **feature/**
 1. Hotfixes MUST be prefixed with **hotfix/**
 1. Releases MUST be pulled together in a branch prefixed with **release/**
 1. **Staging** and **development** MUST never be merged, or branched from.
 1. Branches should be cleaned up post deployment

### Support Workflow Diagram

![LogicSpot GIT Workflow](https://github.com/LogicSpot/LogicSpot-Guidelines/tree/master/git/gitflow.png)
This diagram was created using [draw.io](https://www.draw.io/), this directory contains an .xml file you can upload to amend the image.

## Project Workflow

## Project Rules

 1. Work MUST be branched off of **staging**
 1. Epic branches MUST be prefixed with **epic/**
 1. Feature branches MUST be prefixed with **feature/**
 1. Hotfix branches MUST be prefixed with **hotfix/**
 1. Release branches MUST be pulled together in a branch prefixed with **release/**
 1. Epic branches should be used until that sprint is completed, and then feature branches used for smaller follow up pieces of work/fixes
 1. Releases should follow the following number convention: v{project-number}.{sprint-number}.{release-number}(optional .{release-fixes-number})
 1. All releases should be tagged with the version number (see above) and a description of the release
 1. Branches should be cleaned up post deployment