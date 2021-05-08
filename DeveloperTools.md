## Git

I try to use a `feature->develop->main` git approach.  I'll move to git-flow one day if it becomes necessary.  Releases should tagged using semantic `major.minor.increment`.  This is mostly true however occasionally I'll do a simple `develop->main`.  

I don't use rebase. I squash my commits when merging a feature to develop, once some features are in develop I'll have a moment of madness and decide the release is ready then merge to main and tag.

- `main` should always be the latest tagged release, functional and stable.  This means any vanilla `git clone` should always work out of box as the last best version.
- If I want verison `1.2.3`, there's a tag for that.
- `develop` should always be stable, meaning a `git checkout develop` should always work.
- features should have `develop` merged **onto** them so conflicts happen on the feature prior to merging onto develop.
- features don't have to compile or work as they are in development.
- feature branches must be named `features/XXX` so they can be tracked
- bugs must be named `bugs/XXX` similarly
- a feature should be merged `--squash` conflict-free to develop via a PR, the CHANGELOG should be updated with the branch, feature, commit hash, the feature branch deleted
- develop merges to `main` conflict-free 
- develop contains single squashed commits of features
- `main` contains single squashed commits of develop as releases

**All** commits will follow this.  

## Features

A feature is a piece of work that can include

- unique id
- entry in TODO.md
- documentation
- changelog entry
- user guide
- tests
- implementation

## Issue Tracking

I keep a [TODO.md](TODO.md) with a massive table in it.  I might make my own issue tracker at this rate, or just move to github issues.  The issue, hah, is I tend to do adhoc development on a train with no real wifi so I have a paper-based approach of the TODO.  Each issue will get an ID, the feature branch will be that ID.

The TODO, DOING, DOING and CHANGELOG are where ticket is moved around to currently.

### Starting a feature

	git checkout develop
	git pull origin develop
	git checkout -b features/123

### Starting a bugfix

	git checkout develop
	git pull origin develop
	git checkout -b bugs/123

## Releasing

A release candidate is made from develop,

	git checkout develop
	git pull origin develop
	git checkout -b releases/1_0_0_RC

This can be tested and worked on until it is deemed good.  Once it is good, we

- merge the RC Back over develop 
- merge develop over main
- tag the release
- delete the RC branch

At that point the branches would be `main, develop` and any in-progress features/bugs only - branches are deleted once they are completed.

## Versioning

Semantic versioning for the software, ascending integer for the docker images.

