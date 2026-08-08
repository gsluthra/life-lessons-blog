+++
title = "Jump-Kick: A Faster Way to Switch Tabs in Firefox"
description = "Extension to jump between tabs with a keyboard shortcut and fuzzy search."
author = "Gurpreet Luthra"
date = 2026-03-11T07:30:50Z
images = ["/images/general/jump-kick-blog/1_light-theme-screenshot.jpg"]


tags = [
    "productivity",
    "firefox",
    "opensource",
    "software"
]

+++

![Jump-Kick popup in action](/images/general/jump-kick-blog/1_light-theme-screenshot.jpg "Jump-Kick: quick tab switcher for Firefox")

## Introduction

Over the last few years, I’ve often found myself with **far too many tabs** open in Firefox. Jumping between them usually meant scanning a crowded tab bar, or cycling through windows and hoping I landed on the right one. This is especially true when my screen is shared. I don't want others to see private tabs, or waste time searching for tabs, and interrupt the conversation flow. I wanted something closer to a _command palette_ or _spotlight for mac_ for my browser.

So I built **Jump-Kick**, a small Firefox extension that lets you hit a shortcut, type a few letters, and instantly jump to the tab you want.

## What Jump-Kick does

- **Fuzzy search across open tabs**  
  Type part of a title or URL and Jump-Kick narrows down matching tabs.

- **Keyboard-first workflow**  
  Open the palette with a shortcut, use ↑ ↓ to move, and press **Enter** to switch.

- **Quick sort commands**  
  Type `sort` to see commands that sort your tabs by **URL**, **domain**, **title**, or **last accessed**.

## How to install

You can install Jump-Kick directly from the Firefox Add-ons site: [Jump-Kick – Quick Tab Switcher for Firefox](https://addons.mozilla.org/en-US/firefox/addon/jump-kick-quick-tab-switcher/)

![Jump-Kick icon](/images/general/jump-kick-blog/jump-kick-icon.png ".")

Once installed, look for the default shortcut (on most setups: `Command + Shift + Space` on macOS or `Ctrl + Shift + Space` on Windows/Linux). You can customise this in Firefox’s extension shortcut settings.

## Using Jump-Kick day to day

My own usage is simple:

- Hit the shortcut whenever I catch myself hunting through the tab bar.
- Type a few characters of the tab I have in mind and press **Enter**.
- Occasionally type `sort` to quickly tidy up tabs by URL, domain, title, or “last accessed” order.

If you live in your browser and juggle multiple projects or contexts, I hope Jump-Kick makes switching tabs feel just a bit more calm and deliberate.

Try it out. And if you have an improvement suggestion, do let me know. 

## On Github
Github: https://github.com/gsluthra/jump-kick