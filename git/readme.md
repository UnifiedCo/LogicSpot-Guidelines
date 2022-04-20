# LogicSpot GIT Workflow

## Table of Contents

 1. [Support Workflow](#support-workflow)
    - [Support Rules](#support-rules)
    - [Support Diagram](#support-workflow-diagram)
 1. [Project Workflow](#project-workflow)
    - [Project Rules](#project-rules)

## Support Workflow

This is for projects which have master branch, project is live

### Support Rules

 1. Work MUST be branched off of **master**
 1. Feature branches MUST be prefixed with **feature/**
 1. Hotfixes MUST be prefixed with **hotfix/**
 1. Releases MUST be pulled together in a branch prefixed with **release/**
 1. **Staging** and **development** MUST never be merged, or branched from.
 1. Branches should be cleaned up post deployment

### Support Workflow Diagram

![LogicSpot GIT Workflow](https://raw.githubusercontent.com/LogicSpot/LogicSpot-Guidelines/master/git/gitflow.png)

This diagram was created using [draw.io](https://www.draw.io/), this directory contains an .xml file you can upload to amend the image.

## Project Workflow

Project workflow is only for NEW projects, where master branch is not present, not for existing projects!

## Project Rules

 1. Work MUST be branched off of **staging** (where master branch is not present)
 1. Epic branches MUST be prefixed with **epic/**
 1. Feature branches MUST be prefixed with **feature/**
 1. Release branches MUST be pulled together in a branch prefixed with **release/**
 1. Epic branches should be used until that sprint is completed, and then feature branches used for smaller follow up pieces of work/fixes
 1. Releases should follow the following number convention: MAJOR.MINOR.VERSION e.g. 1.1.0, then 1.2.0, then hotfix version would be 1.2.1
 1. All releases should be tagged with the version number (see above) and a description of the release
 1. Feature branches should be cleaned up post deployment


