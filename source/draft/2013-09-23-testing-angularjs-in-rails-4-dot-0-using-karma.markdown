---
layout: post
title: "Testing AngularJS in Rails using Karma"
date: 2013-09-23 19:18
comments: true
categories: AngularJS
published: false
---

## Introduction
This post explains how to setup [karma](karma-runner.github.io) and get started with testing your [Angular](angularjs.org) application in Rails 4.0 framework.

## What you should already have in your system
* ruby 1.9.3+
* Rails 3.2+
* Node/NPM


Create a rails project
```
rails new angularjs_karma_rails --skip-active-record -T
```

Initialize npm
```
npm init .
```
* app name (Enter)
* version: 0.0.1 (optional)
* description: (optional)
* entry point: (enter)
*