DEPLOYMENT
==========

"*Software deployment is all of the activities that make a software system
available for use.*" [Wikipedia]

In the software development world, we frequently encounter the terms "deploy"
and "release". Occasionally, these terms are used interchangeably but,
in the context of this guide, we'll stick to the common usage where
**Release** is the act of making a software version available for users and
**Deployment** is the [more technical] process of installing and configuring a
version of software onto a target environment.

Depending on the system complexity and the number of underlying interacting
components, the deployment process may potentially be intricate and error-prone.
That being the case, it's important to execute it methodically while adhering
to industry best practices.

Following are a few guidelines and points to think about before releasing
code to production:


Process
-------
* Devise a release plan and deployment protocol - make sure it's clearly
  documented so anyone can apply it.
* When possible, opt for continuous deployment - as the saying goes:
  "*if it hurts, do it more often*" (a.k.a lean into the pain).
* Consider the differences between a fresh install and code upgrade.
  Make sure your deployment protocol supports both (always prefer an
  agnostic process).
* When applying a more traditional approach, consider minor/major versioning -
  make sure to tag and branch the source code repo.
* Instruct a code freeze when applicable (typically when releasing
  a major version).
* Make sure your deployment protocol is reversible (i.e. allow rollback).
  This should include all parts of the code, relevant data and DB changes.
  Make sure your deployment processes are re-runnable (including DB scripts).


Environments
------------
* Always maintain separated and isolated environments - DEV, TEST and PROD.
* When possible (typically when data QA is a factor) run a PRE-PROD or an
  INTEGRATION environment that is identical to prod in all aspects.
* Resist the temptation to manually work/fix/configure the PROD environment.
  Nothing good ever comes from doing so.
* As a part of the deployment process, assert dependencies/requirements and
  verify that all required services are up and aligned.
* Optionally, use some kind of feature releasing mechanism (e.g. feature flags).
* Automate environment settings and configuration management (use a dedicated
  tool or create configuration scripts when needed).
* Pay attention to scale (deploying clusters) and recovery environments
  (DR and replicated environments). Are they automatically replicated?
* Do not allow manual code editing when deploying the project to a new environment.
  Separate environment settings from code.


DBs
---
* Keeping your DBs in sync is always a pain in the butt but, difficult as it is,
  integrate DDLs and DB changes into the deployment processes.
* Support a DB init (on a fresh install) as well as DB changes (i.e. alters).
* Make sure all DB changes are reversible. When possible, contain all changes
  in a single transaction that can be rolled-back in case of failure.


Tests and Code Quality
----------------------
* Always be testing!
* Automate unit and smoke tests as well as regression tests.
* Before deploying, verify that all source code meets the projects' coding
  standards. Auto-run style checks.


Tools
-----
* Establish an automated deployment process - there are many industry standard
  tools suitable for the task (e.g. TeamCity, Jenkins).
* Use a deployment and configuration management system.
* Consider using Docker.


Monitoring
--------------
* Monitor the deployment processes and run auto health check(s) after each step.
* Integrate alerts and notifications into the deployment process.


Documentation
-------------
* Before deploying, verify that user documentation matches the current release.
* Write detailed release notes - clearly list new features, general
  improvements, bug fixes and known issues (i.e. existing limitations and known bugs).


Team and PR
-----------
* Make sure all team members are able to monitor the deployment status
  (e.g. failed components, rollback status etc.)
* [Auto-] Announce a maintenance window. If down time is required, make sure
  all users are onboard.
* When releasing a major version, announce it within the organization (PR).
  Let users know what they may expect from the new version (in terms of
  new features, fixed bugs etc.)
