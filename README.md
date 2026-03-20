# Decentraland Explorer Workspace

A unified workspace containing the Explorer desktop client and its related libraries for the Decentraland platform. This repository uses **Git Submodules** to aggregate multiple repositories, making it easier to work across projects during development.

---

## 📦 Submodules Overview

### Core Client & Launcher

Desktop client and launcher for Decentraland 2.0.

| Submodule | Description |
|-----------|-------------|
| **[unity-explorer](unity-explorer/)** | Desktop client — Unity 6 application for exploring and interacting with the Decentraland metaverse |
| **[launcher-rust](launcher-rust/)** | Desktop launcher — Rust/Tauri app that manages installation, updates, and launching of the Explorer client |

### Avatar & Previews

Avatar rendering and wearable preview services.

| Submodule | Description |
|-----------|-------------|
| **[aang-renderer](aang-renderer/)** | Avatar renderer — WebGPU-based preview renderer for avatars and wearables in the marketplace |

### Runtime & Scripting

Libraries that power scene execution, communication, and JavaScript interop.

| Submodule | Description |
|-----------|-------------|
| **[protocol](protocol/)** | Decentraland protocol — protobuf definitions for SDK components, services, and comms |
| **[rpc-csharp](rpc-csharp/)** | RPC library — C# transport layer for communication between systems |
| **[ClearScript](ClearScript/)** | JavaScript engine — V8-based scripting for scene runtime execution in Unity |
| **[client-sdk-unity](client-sdk-unity/)** | LiveKit SDK — real-time voice and video communication for Unity |

```
unity-explorer (Client)
    ├── protocol (Protobuf definitions)
    ├── rpc-csharp (RPC transport)
    ├── ClearScript (JS engine)
    └── client-sdk-unity (Voice/Video comms)
```

### Shared Libraries

Cross-cutting packages used by the explorer and related tools.

| Submodule | Description |
|-----------|-------------|
| **[unity-shared-dependencies](unity-shared-dependencies/)** | Shared package — GLTF importer wrappers, custom shaders, and wearable utilities |
| **[unity-gltf](unity-gltf/)** | glTF loader — imports glTF/GLB 3D models into Unity (fork of glTFast) |
| **[chrome-devtool-protocol-unity](chrome-devtool-protocol-unity/)** | DevTools protocol — Chrome DevTools integration for debugging scenes in Unity |
| **[Unity3D-NSubstitute](Unity3D-NSubstitute/)** | Test mocking — NSubstitute packaged for Unity's test framework |

### Tooling

Offline conversion and asset processing.

| Submodule | Description |
|-----------|-------------|
| **[asset-bundle-converter](asset-bundle-converter/)** | Asset converter — converts glTF/GLB models to Unity AssetBundles for optimized loading |
| **[metamorph](metamorph/)** | Media converter — converts images and videos into Explorer-friendly formats (KTX2 and MP4) |

---

## 🚀 Getting Started

### Prerequisites

- Git 2.13+ (for improved submodule support)
- Unity 6000.2.6f2
- Node.js 20.x+ (for protocol generation scripts)

### Cloning the Repository

**Clone with all submodules:**

```bash
git clone --recurse-submodules git@github.com:decentraland/explorer-workspace.git
cd explorer-workspace
```

**If you already cloned without submodules:**

```bash
git submodule update --init --recursive
```

---

## 📚 Essential Git Submodules Commands

### Updating Submodules

```bash
# Update all submodules to their latest remote commits
git submodule update --remote --merge

# Update a specific submodule
git submodule update --remote --merge <submodule-path>

# Pull latest changes in parent repo AND update submodules
git pull --recurse-submodules
```

### Working Inside a Submodule

```bash
# Navigate into the submodule
cd <submodule-path>

# Work normally with git (checkout, branch, commit, push)
git checkout main
git pull origin main

# Make changes and commit
git add .
git commit -m "Your changes"
git push origin main
```

### After Making Changes in a Submodule

```bash
# Go back to the parent repository
cd ..

# The parent repo will show the submodule as modified
git status

# Stage the submodule reference update
git add <submodule-path>

# Commit the updated submodule reference
git commit -m "Update <submodule-name> to latest version"

# Push parent repo changes
git push
```

### Workflow Example: Work on a Specific Tool

```bash
# Navigate to the library
cd unity-gltf

# Create a feature branch
git checkout -b feature/my-new-feature

# Make your changes, then commit and push
git add .
git commit -m "feat: add new feature"
git push origin feature/my-new-feature

# Create a PR in the submodule repository
# After merge, update the parent repo reference
cd ..
git submodule update --remote unity-gltf
git add unity-gltf
git commit -m "chore: update unity-gltf with new feature"
git push
```

---

## 🤝 Contributing

Each submodule has its own contribution guidelines. Please refer to the individual repository's `README.md` and `CONTRIBUTING.md` files for specific instructions.

## 📄 License

Each submodule may have its own license. Please check the individual repositories for license information.
