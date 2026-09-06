# 🚀 RepoGrabber

<p align="center">
  <img src="public/logo.jpeg" alt="RepoGrabber logo" width="120" />
</p>

<p align="center">
  <strong>A simple way to download public GitHub code without Git or the command line.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white" alt="React 18" />
  <img src="https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
</p>

## 💡 Overview

**RepoGrabber** is a frontend web application for retrieving content from **public GitHub repositories**. It accepts a GitHub repository, folder, or file URL and provides a straightforward interface for browsing and downloading the selected content.

The application removes the need to install Git, use a terminal, or run commands such as `git clone`. It is useful when the goal is simply to obtain public source code, a particular folder, or a single file.

> 🔒 **Scope:** RepoGrabber works with publicly accessible GitHub content through the GitHub REST API. It does not authenticate users or access private repositories.

## 🎯 Problem solved

GitHub is an essential source of open-source code, learning materials, templates, and project assets. However, the standard way to retrieve a repository often requires Git knowledge and a local development environment.

RepoGrabber solves this accessibility problem by presenting a browser-based workflow. It makes GitHub content easier to retrieve for:

- 🎓 **Students and learners** who need examples or starter projects.
- 👤 **Non-technical users** who do not work with Git or command-line tools.
- 💻 **Developers** who need one file or one directory rather than a complete clone.
- 🖥️ **Users on temporary or restricted computers** where installing development tools is not practical.

Instead of cloning an entire repository through the terminal, users can paste a GitHub URL and download only the content they need.

## ✨ Core capabilities

| Capability | Description |
| --- | --- |
| 📦 **Repository downloads** | Downloads a repository’s default branch as a ZIP archive. |
| 📁 **Folder downloads** | Packages a selected public directory and its nested contents into a ZIP archive in the browser. |
| 📄 **Single-file downloads** | Retrieves a file directly from its public GitHub download URL. |
| 🔎 **Repository exploration** | Displays public files and folders, supports directory navigation, and includes breadcrumbs. |
| 👀 **File preview** | Provides a desktop preview experience for supported files before download. |
| 🕘 **Recent-download history** | Keeps recent download records in the browser for convenient repeat access. |
| 🌗 **Responsive themed UI** | Supports mobile layouts and light/dark appearance modes. |

## ⚙️ Application flow

```text
GitHub URL
    ↓
URL parser identifies repository, folder, or file
    ↓
GitHub REST API returns public metadata and content
    ↓
RepoGrabber renders the explorer or retrieves the selected file
    ↓
Browser downloads the file/archive, or JSZip creates a folder archive
    ↓
Recent-download metadata is saved in localStorage
```

The application runs entirely in the browser for its standard workflow. Public GitHub data is requested directly from the GitHub API, selected-folder archives are created client-side, and recent-download history remains on the user’s device.

## 🔗 Supported GitHub URL types

```text
# Repository
https://github.com/owner/repository

# Folder
https://github.com/owner/repository/tree/main/path/to/folder

# File
https://github.com/owner/repository/blob/main/path/to/file.ext
```

Repository URLs ending in `.git` are also recognized.

## 🛠️ Tools and technologies

| Area | Technology | Role |
| --- | --- | --- |
| Frontend framework | **React 18** | Builds the interactive user interface and application components. |
| Programming language | **TypeScript** | Provides type safety for UI state, GitHub API responses, and utilities. |
| Build tool | **Vite** | Powers fast development and optimized production builds. |
| Styling | **Tailwind CSS** | Provides responsive, utility-first styling. |
| UI components | **shadcn/ui** and **Radix UI** | Supplies accessible interface primitives including inputs, dialogs, cards, buttons, and toasts. |
| Icons | **Lucide React** | Provides consistent icons throughout the interface. |
| Routing | **React Router** | Handles navigation between the main, guide, about, and fallback pages. |
| API integration | **GitHub REST API** | Retrieves public repository details, directory contents, and file metadata. |
| Archive generation | **JSZip** | Creates downloadable ZIP files for selected folders in the browser. |
| Local persistence | **localStorage** | Stores recent-download metadata in the current browser. |
| Page metadata | **React Helmet Async** | Manages titles, descriptions, and canonical metadata. |

## 🗂️ Project architecture

```text
src/
├── components/
│   ├── RepoExplorer.tsx       # Repository browsing and download workflow
│   ├── SearchBox.tsx          # GitHub URL entry
│   ├── FileList.tsx           # File and folder listing
│   ├── FilePreview.tsx        # Supported-file preview
│   ├── RecentDownloads.tsx    # Browser-based history
│   └── layout/                # Navigation, footer, and theme controls
├── hooks/
│   ├── useGitHubApi.tsx       # GitHub REST API integration
│   └── useLocalStorage.tsx    # Persistent browser-state utility
├── utils/
│   └── gitHubUtils.ts         # URL parsing and file helpers
├── pages/                     # Main, guide, about, and 404 pages
└── contexts/                  # Theme state
```

## 🔐 Privacy and limitations

- **Public repositories only:** private repositories and protected content are outside the application’s scope.
- **GitHub API rate limits:** unauthenticated GitHub API requests can be temporarily limited after heavy use.
- **Client-side archive creation:** large folders may take longer to package and can require significant browser memory.
- **Local-only history:** Recent Downloads are saved in the active browser and are not synchronized to a server or account.
- **License responsibility:** downloading code does not change its license or attribution requirements.

## 📌 Summary

**RepoGrabber makes public GitHub content more accessible.** It replaces terminal-based cloning with a clear web interface for browsing and downloading repositories, folders, and files—without requiring Git installation or command-line experience.
