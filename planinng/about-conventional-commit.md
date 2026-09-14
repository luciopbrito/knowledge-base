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

The Conventional Commits are way to define commit message with a better approach following the SemVer.
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

- type: The type must represent the main proposal about the commit.

  Conventional Commit in its root, supports only two type: `feat` and `fix`. In this content has an entire title about
  them.

- optional scope: The scope must represent the part of the software/implementation you are working on.

  Conventional commit indicates that the `scope` is optional. Because it depends on the work that you are doing.
  Then, you must know what you are doing to use the scope.

- description: The description must represent the main idea about what you are doing.

  Conventional commit indicates that the description must be easy and go straight to the point. If you need to
  explain more, use the body section for it.

- optional body: Use the body section only if you want to discuss about the commit details. Nothing more.

  Conventional commit indicates that the body can be used for specifying the commit.

- optional footer: Use the footer section only if there are `BREAKING CHANGES` or `Refs` for the commit.

## Commit types

The type is where the Conventional Commits take advantage. The type proposal is to keep the history easier to
understand. There are insights for it below.

### feat

The feat type must be used for new features and implementations. About the SemVer, they are part of MINOR (x.X.x). There
are examples below.

```txt
feat(auth): add password reset

Allow users to request a password reset email.
```

- The commit will be published: Supporting password reset for the users.
- The commit scope is `auth` because the implementation refers to authentication.
- The commit body specifies the description.

### fix

The fix type must be used for fixing something wrong that refers to the software. About the SemVer, they are part of PATCH
(x.x.X). There are examples below.

```txt
fix(api): handle invalid token
```

- The commit will be published: Fixing the invalid token error.
- The commit scope is `api` because the implementation refers to the API.

### Common additional types

The Conventional commit supports only two types: `feat` and `fix`. However, the worldwide projects adopted additional
types to improve things and keep them more organized.

**Note: The Conventional Commit creators do not support the additional types.**

#### build

The build type must be used for changes related to the building project. (e.g. dependencies, scripts to build the
application, etc). There are examples below.

```txt
build: add package-1 to dependencies

The package-1 brings the necessary behavior for the application.
```

- The commit will be published: An extra package for supporting the application.
- The commit body specifies the description.

#### ci

The ci type must be used for changes that affect the pipeline files. (e.g. `.github/workflows/`, `.gitlab-ci.yml`, etc).
There are examples below.

```txt
ci(dev): improving the dev pipeline

The dev pipeline needs extra steps.
```

- The commit will be published: Improving the dev pipeline.
- The commit scope is `dev` because it is related with Dev stage of DevSecOps.
- The commit body specifies the description

#### chore

The chore type must be used for changes that do not impact the code logic at all. (e.g. Improving lint, adding tool to
improve the development, etc). There are examples below.

```txt
chore(lint): change rule for quotation

The project must follow the doubles quote approach in its files.
```

- The commit will be published: changing the rules for quotation
- The commit scope is `lint` because it is related to lint tool.
- The commit body specifies the description.

#### docs

The docs type must be used for changes that affect documentation files. (e.g. Improving README.md, Adding how to use the
new functionality, etc). There are examples below.

```txt
docs(api): add example to get user resources

The documentation must be updated to explain how to produce an user resource.
```

- The commit will be published: Documentation updated about user resource.
- The commit scope is `api` because it is related to the API layer.
- The commit body specifies the description.

#### perf

The perf type must be used for changes that are related to performing the code. (e.g. Changing for statement to while,
etc). There are examples below.

```txt
perf(products): change to a while approach to get products

The while statement is the best approach according to Big O notation.
```

- The commit will be published: Improving the way of getting products.
- The commit scope is `products` because it is related to the product layer.
- The commit body specifies the description.

#### test

The test type must be used for changes that are related to specification, unit, and e2e (end-to-end) files. (e.g. Karma files
for Angular, .NET Unit tests, etc). There are exemples below.

```txt
test(auth): add the suit test for the auth service

To follow the TDD architecture. It is necessary to define the auth service test before starting the implementation. 
```

- The commit will be published: Adding the suit test for the development based on it.
- The commit scope is `auth` because it is related to the auth testing.
- The commit body specifies the description.

#### style

The style type must be used for changes that are related to clean/pretty the code. (e.g. Removing the spaces, Removing
the comments, etc). There are exemples below.

```txt
style(auth): remove the comments about testing
```

- The commit will be published: Less comments. Keeping the code base clean.
- The commit scope is `auth` because it is related to the auth layer.

#### revert

The revert type must be used when the changes are related to the `git revert` command. In other words, when the
commit reverts another commit.

```txt
revert: "fix(macos-latest): add the jq"

This reverts commit e9568ce.
```

- The commit will be published: Reverting the changes about "fix(macos-latest): add the jq"
- The commit body specifies the description.

#### refactor

The refactor type must be used when the changes do not change the current state of the codebase. Plus, it improves the implementation technique. (e.g. Refactoring the function to respect the architecture, Changing the function after code-review, etc)

```txt
refactor(repository): improve the user's select statement

After discuss about Big O Notation, the user's select statement update is mandatory.
```

- The commit will be published: Improving the select statement.
- The commit scope is `repository` because it is related to the repository layer.
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

The scope is optional because it depends on the context that you are doing. Use only if you have a clear idea of the
context. For example, let's discuss about a Web API project with DDD architecture.

There are common contexts that allow you understand the scope easily (e.g. domain, infrastructure, repository, services,
etc). Therefore, you can use them as scope. You only need to have in mind that there are no rules for scopes.
During the development, you can recognize the parts that make sense to use as scope.

## About Description

The description part tries to resolve the common problem of defining a commit. The description must define in some words
what changes the commit will resolve. Keep in mind, the description must be small. If it would be
necessary to describe more about the changes. Then, you must use the body section for it.

## About Body

The body part is the place where you can describe more about the changes. Keep in mind to use the body section when the
changes are big or when you have an extra explanation.

## About Footer

The footer part must be used for **Breaking Changes** or **to add references to the commit**. (e.g. mentioned reviews
links, related commits, etc).

## About Breaking changes

A breaking change is a commit related to breaking compatibility. In other words, the changes that are related to
the public API can break backward compatibility with existing consumers. About the SemVer, they are part of MAJOR
(X.x.x).

In the past, it developed the feature below.

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

Choosing a type is hard to understand. Mainly, if you do not know the meaning about the types. The main types are `feat`
and `fix`. Think of them as a **rule** that you must follow in every step ahead related to the software.

The others have a specific situation to use them. For that reason, during a feat/fix development can occur a lot of
changes like: adding some dependencies (build), defining a specification to test (test), and adding some documentation
(docs).

At end of the work, you can define: removing unnecessary code (style), improving the code writing by review (refactor),
improve code workflow with a better approach (perf), adding a pipeline to improve a specific workflow (ci).

## Good and bad examples

The good examples for Conventional Commit are those that respect the meaning of the type and, of course, use at least
the mandatory fields (type and description). The scope idea must be kept in mind as well. Because when you can recognize
part of the implementation, it is a good sign that you are doing the job well.

## Relationship with Semantic Versioning

The Semantic Versioning is an approach that makes your software better. In other words, it is a distinction between
software guiding for nonsense and software guiding for features and breaking changes. The conventional commit made
Semantic Versioning easier to implement. Focus on commits that explain themselves.
