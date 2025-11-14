# .NET Version Update Instructions

## For Humans

**This file is designed to be used with AI coding assistants (like GitHub Copilot, Claude, ChatGPT, etc.)**

To update this template to a newer .NET version:
1. Open this file in your IDE with an AI assistant enabled
2. Ask the AI: "Update this project to .NET [VERSION] using the instructions in UPDATE_INSTRUCTIONS.md"
3. The AI will use the instructions below to update all necessary files

---

## For AI Tools

When asked to update this project to a new .NET version, perform the following updates:

### 1. Project Files (.csproj)
Update the following files:
- `src/NetDaemon.Templates.Project/NetDaemon.Templates.Project.csproj`
- `src/NetDaemon.Templates.Project/templates/netdaemon/NetDaemonApps.csproj`
- `src/NetDaemon.Templates.Project/templates/netdaemon_src/Debug.csproj`

**Changes required:**
- Update `<TargetFramework>` to the new .NET version (e.g., `net11.0`)
- Update `<LangVersion>` to the corresponding C# version:
  - .NET 10 → C# 14.0
  - .NET 11 → C# 15.0
  - .NET 12 → C# 16.0
  - (Pattern: .NET version - 4 = LangVersion offset from C# 10.0)

### 2. Dockerfiles
Update the following files:
- `src/NetDaemon.Templates.Project/templates/netdaemon/Dockerfile`
- `src/NetDaemon.Templates.Project/templates/netdaemon_src/Dockerfile`

**Changes required:**
- Update `FROM mcr.microsoft.com/dotnet/sdk:X.0` to new version
- Update `FROM mcr.microsoft.com/dotnet/aspnet:X.0` to new version

### 3. VS Code Launch Configurations
Update the following files:
- `src/NetDaemon.Templates.Project/templates/netdaemon/.vscode/launch.json`
- `src/NetDaemon.Templates.Project/templates/netdaemon_src/.vscode/launch.json`

**Changes required:**
- Update debug paths from `bin/Debug/netX.0/` to new version

### 4. GitHub Actions Workflows
Update the following files:
- `.github/workflows/tags_nuget.yml`

**Changes required:**
- Update the step name `Install .Net X` to new version
- Update `dotnet-version: "X.0.x"` to new version

### 5. Verification Steps
After making changes:
1. Search for any remaining references to the old version (e.g., `net9.0`, `net10.0`)
2. Check for any hardcoded SDK version numbers
3. Verify all Dockerfiles reference the same version
4. Ensure GitHub Actions and project files are consistent

### Example Update Pattern
When updating from .NET 10 to .NET 11:
- `net10.0` → `net11.0`
- `LangVersion>14.0` → `LangVersion>15.0`
- `dotnet/sdk:10.0` → `dotnet/sdk:11.0`
- `dotnet/aspnet:10.0` → `dotnet/aspnet:11.0`
- `bin/Debug/net10.0/` → `bin/Debug/net11.0/`
- `dotnet-version: "10.0.x"` → `dotnet-version: "11.0.x"`

---

## Version History
- 2025-11-14: Updated to .NET 10 / C# 14.0
- Previous: .NET 9 / C# 13.0
