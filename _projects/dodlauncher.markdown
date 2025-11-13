---
layout: project
title: DoD Launcher
description:  Launcher for the game Day of Despair
---

# DoD Launcher

## Overview

For ease of distribution and due to the complaints of GitHub downloading for end users, I knew Day of Despair would need a launcher that both allowed control over installations of the game while also providing an easy to use interface for getting builds of the game with little resistance and navigation.

## Features

- **News Fetching** - Latest release notes of the game are fetched using the C# System.Net HttpClient class and displayed to the user informing them of any new releases.

- **Instance Management** - Much like the Minecraft Java launcher, the Day of Despair Launcher uses and instance system that specifies the game version, and any arguments for that game as well as a name to quickly reference it by. This allows users to play older versions of the game easily and experiment with command-line arguments should they desire.

- **Automatic Downloading & Installation** - Users attempting to launch an instance that is not downloaded will fetch and download the build from GitHub and extract its contents with progress bars to show the current progress of each step. Afterwards, it will start the game up with any of the arguments specified in the instance.

- **MVVM** - The launcher uses the Model View View-Model pattern to keep functionality separate from the visuals as well as keep track of data across views such as going from the "Instance Creation" window back to the "Main Window".

## Technical Callenges

- **GitHub API** - There was a learning curve when it came to using HttpClient, that being understanding the JSON format of both repositories which are JSON objects and releases which are stored as an array of objects owned by the repository. Its obvious now but I took me a hot minute to realize that. Furthermore, I also did not initially know that you could view the data in a formatted manner by using the link in a web browser. I found it when trying to download the game data but accidentally downloading the repository JSON object instead and reading the contents (unformatted I should add) in a text editor.