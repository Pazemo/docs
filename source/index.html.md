---
title: Pazemo Docs

language_tabs:
  - shell: cURL
  - php: PHP
  - javascript: JavaScript
  - python: Python

toc_footers:
  - <a href='https://pazemo.com/signup'>Sign Up for a API Key</a>
  - <a href='http://docs.stg.pazemo.com/'>Pazemo API Explorer</a>

includes:
  - getting_started
  - api_access
  - users
  - accounts
  - recipients
  - withdraw
  - ping
  - errors

search: true

code_clipboard: true
---

# Introduction

The Pezemo API is organized around REST. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

You can use the Pazemo API in test mode, which does not affect your live data or interact with the banking networks. The API key you use to authenticate the request determines whether the request is live mode or test mode.