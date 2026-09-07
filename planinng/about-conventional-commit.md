# About Conventional Commits

## Table of content

- [What are Conventional Commits?](#what-are-conventional-commits)
- [Commit message structure](#commit-message-structure)
- [Commit types](#commit-types)
  - [feat](#feat)
  - [fix](#fix)
  - [Common additional types](#common-additional-types)
    - [build](#build)
    - [ci](#ci)
    - [chore](#chore)
    - [docs](#docs)
    - [perf](#perf)
    - [test](#test)
    - [style](#style)
    - [revert](#revert)
    - [refactor](#refactor)
  - [Quick Guide](#quick-guide)
  - [Decision Guide](#decision-guide)
- [About Scope](#about-scope)
- [About Description](#about-description)
- [About Body](#about-body)
- [About Footer](#about-footer)
- [About Breaking changes](#about-breaking-changes)
- [How to choose a type](#how-to-choose-a-type)
- [Good and bad examples](#good-and-bad-examples)
- [Relationship with Semantic Versioning](#relationship-with-semantic-versioning)

## What are Conventional Commits?

The conventional commits are common ways to format the commit message to be clearer and better following the SemVer.
About the SemVer, it is another conventional focus on distributing the software with better versioning.
[For more information](https://semver.org/)

## Commit message structure

The message structure focus on showing the full idea about the commit without losing time to check the code.

```txt
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

So, let's the discuss about the code above...

- type: the type must represent the main proposal about the commit.

  Conventional Commit in its root, support only two type: `feat` and `fix`. In this content has an entire title about
  them.

- optional scope: the scope must represent the part of the software/implementation you are working on.

  Conventional commit indicates that the `scope` is an optional. Because, it depends on the part that you are working on
  it. The point is... You must know what are you doing to use the scope.

- description: the description must represent the main idea about what you are doing.

  Conventional commit indicates that the description must be easy and straight to the point. If you would need to
  explain more, use the body part to it.

- optional body: the body must use only if you want to discuss about the details for the commit. Nothing more.

  Conventional commit indicates that the body can be use for specification about the commit.

- optional footer: the footer must use only if there are `BREAKING CHANGES` or `Refs` for the commit.

## Commit types

The type is where the conventional commits take advantage. The type proposal is to keep the history easier to
understand. So, below there are insights to it.

### feat

The feat type must be used for new features and implementations. About the SemVer, they are part of MINOR (x.X.x). So,
There are examples below.

```txt
feat(auth): add password reset

Allow users to request a password reset email.
```

- The commit will be released with: Supporting password reset for the users.
- The commit scope is `auth` because the part of implementation is about the authentication.
- The commit body specifies the description.

### fix

The fix type must be used for fixing something wrong about the software. About the SemVer, they are part of PATCH (x.x.X).
So, there are examples below.

```txt
fix(api): handle invalid token
```

- The commit will be released with: Fixing the invalid token error.
- The commit scope is `api` because the part of implementation is about the API.

### Common additional types

The Conventional commit supports just two types: `feat` and `fix`. However, the world wide projects adopted some
additional types to improve the things and keep more organized.

**Note: The commit additional types are not support by conventional commit creators.**

#### build

The build type must be used for changes related to the building project. (e.g. dependencies, scripts to build, etc).
There are examples below.

```txt
build: add package-1 to dependencies

The package-1 brings the necessary behavior for the application.
```

- The commit will be released with: An extra package to support the application.
- The commit body specifies the description.

#### ci

The ci type must be used for commit that changes pipeline files. (e.g. `.github/workflows/`, `.gitlab-ci.yml`, etc).
There are examples below.

```txt
ci(dev): improving the dev pipeline

The dev pipeline must use the extra steps.
```

- The commit will be released with: Improving the dev pipeline.
- The commit scope is `dev` because it is related with Dev part of DevSecOps concept.
- The commit body specifies the description

#### chore

The chore type must be used to changes that are not impact the code logic at all. (e.g. Improving lint, add tool to
improving the development, etc). There are examples below.

```txt
chore(lint): change rule for quotation

The project must follow the doubles quote approach in its files.
```

- The commit will be released with: changing the rules for quotation
- The commit scope is `lint` because is related to lint tool.
- The commit body specifies the description.

#### docs

The docs type must be used to changes that affect files about documentation. (e.g. Improve README.md, Add how to use the
new functionality, etc). There are examples below.

```txt
docs(api): add example to get user resources

The documentation must be updated to explain how to produce an user resource.
```

- The commit will be released with: Documentation updated about user resource.
- The commit scope is `api` because is related to the API layer.
- The commit body specifies the description.

#### perf

The perf type must be used to changes related to perform the code. (e.g. Change for statement to while, etc). There are
examples below.

```txt
perf(products): change to while approach to get products

The while statement is the best approach according to Big-O notation.
```

- The commit will be released with: improving the way for getting products
- The commit scope is `products` because is related to the product layer.
- The commit body specifies the description.

#### test

The test type must be used to changes related to: specification, unit, e2e (end to end) files. (e.g. Karma files for
angular, .NET Unit tests, etc). There are exemples below.

```txt
test(auth): add the suit test for auth service

To follow the TDD architecture. It is necessary to define auth service test before starting the implementation. 
```

- The commit will be released with: Adding the suit test to development based on it.
- The commit scope is `auth` because is related to the auth testing.
- The commit body specifies the description.

#### style

The style type must be used to changes related to clean/pretty the code. (e.g. Removing the spaces, Removing the
comments, etc). There are exemples below.

```txt
style(auth): remove the comments about testing
```

- The commit will be released with: Less comments. Keeping the code base clean.
- The commit scope is `auth` because is related to the auth layer.

#### revert

The revert type must be used when the commit's changes are related to the `git revert` command. In other words, when
commit reverts another commit.

```txt
revert: "fix(macos-latest): add the jq"

This reverts commit e9568ce.
```

- The commit will be released with: Reverting the changes about "fix(macos-latest): add the jq"
- The commit body specifies the description.

#### refactor

The refactor type must be used when the commit's changes are not change the current state of the code base. (e.g.
Refactoring the function to respect the architecture, Changing the function after code-review, etc)

```txt
refactor(repository): improve the user's select statement

After discuss about Big-O Notation, the user's select statement update is mandatory.
```

- The commit will be released with: Improving the select statement.
- The commit scope is `repository` because is related to the repository layer.
- The commit body specifies the description.

## Quick Guide

| Type | Use it when... | Example |
| ---- | -------------- | ------- |
| feat | adding a new feature | feat: add password reset |
| fix | fixing a bug | fix: prevent duplicate orders |
| build | changing build system or dependencies | build: upgrade webpack |
| chore | making maintenance changes that don't modify application behavior | chore: update editorconfig |
| ci | changing CI configuration | ci: add Node.js 22 to workflow |
| docs | changing documentation | docs: document authentication API |
| style | changing code formatting/style without changing behavior | style: format user service |
| refactor | restructuring code without changing behavior | refactor: extract payment validator |
| perf | improving performance | perf: optimize product query |
| test | adding or modifying tests | test: add checkout tests |
| revert | reverting a previous commit | revert: revert checkout changes |

## Decision Guide

- Did I add a new feature? → `feat`
- Did I fix a bug? → `fix`
- Did I only restructure existing code without changing behavior? → `refactor`
- Did I improve performance? → `perf`
- Did I add/change tests? → `test`
- Did I change documentation? → `docs`
- Did I change formatting only? → `style`
- Did I change CI configuration? → `ci`
- Did I change build tooling or dependencies? → `build`
- Is it a general maintenance change? → `chore`
- Am I undoing a previous commit? → `revert`
- Does the change break existing API compatibility? → `add ! and/or BREAKING CHANGE`

## About Scope

The scope is optional because depends on the context that you are doing. The tip is... Use only if you have a clear
idea of the context. For example, let's discuss about a Web API project with DDD architecture.

There are common contexts that allow you understand the scope easily (e.g. domain, infrastructure, repository, services,
etc). So, you can use them as scope. You only need to have in your mind that there are not rules for scopes, during the
development you can recognize the parts that make sense to use as scope.

## About Description

The description part tries to resolve the common problem about define a commit. The description must define in some words
what are the changes that the commit will solve. Keep in your mind, the description must be small, and if it would be
necessary to describe more about the changes. Actually, you must use the body part to it.

## About Body

The body part is the place where you can describe more about the changes. So, keep in your mind... Use either the body
part when the changes are big, or the changes must have an extra explanation.

## About Footer

The footer part must be used for **Breaking Changes** or **add references to the commit**. (e.g. mentioned reviews
links, related commits, etc).

## About Breaking changes

The breaking changes are commits related to the breaking compatibility. In other words, breaking changes are changes to
the public API or behavior that are not backward-compatible with existing consumers. About the SemVer, they are part of
MAJOR (X.x.x).

In the past, it has developed the feature below.

```txt
feat(product): the user can create a product without category

Now, the user can create a product without category
```

Now, it must be modified by another feature below.

```txt
feat(product)!: the user must create a product with category

BREAKING CHANGE: When user wants to create a product the category is mandatory.
```

## How to choose a type

Choosing a type is hard to understand mainly if you do not know the meanings about the types. The tip is... The main
types are `feat` and `fix`. Think about them as a **rule** that you must follow in every step forward about the
software.

The others have a specific situation to use them. So, during a feat/fix development can occur a lot of changes like:
adding some dependencies (build), defining specification to test (test), adding some documentation (docs).

At end of the work, you can define: removing unnecessary code (style), improving the code writing by review
(refactor), improve code workflow with better approach (perf), adding a pipeline to improve a specific workflow (ci)

## Good and bad examples

The good examples for conventional commit are that respect the meaning about type, and of course it uses at least the
mandatory fields (type and description). The scope idea must keep in your mind as well. Because when you can recognize
the part of your implementation is a good sign that you are doing the job well.

## Relationship with Semantic Versioning

The Semantic Versioning is an approach that makes your software better. In other words, it is a distinct between a
software guiding for non sense and software guiding for featuring and breaking changes. The conventional commit became
the Semantic Versioning easier to implement. Focus on commits that explain themselves.
