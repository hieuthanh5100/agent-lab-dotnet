# Copilot Workspace Instructions

## Mandatory Development Checklist

Before you consider a change “done”, run these in order:

- Lint/format: `dotnet format --verify-no-changes SocOps/SocOps.csproj`
- Build: `dotnet build SocOps/SocOps.csproj`
- Test: `dotnet test` (if/when tests exist)

## Project

**SocOps** is a Social Bingo game built with **Blazor WebAssembly** targeting **.NET 10**.

## Repo Layout

- `SocOps/` — Blazor WASM app
  - `Components/` — reusable UI components (board, squares, modals, screens)
  - `Pages/` — routable pages (e.g., `Home.razor`)
  - `Services/` — state + game logic
  - `Models/` — state models
  - `Data/Questions.cs` — question bank
  - `wwwroot/css/app.css` — app styling + utility classes
- `docs/` — static workshop site assets
- `workshop/` — workshop steps and guide markdown

## Key Commands (Windows)

Prefer VS Code tasks when available:

- Build: `dotnet build SocOps/SocOps.csproj`
- Run: `dotnet run --project SocOps/SocOps.csproj`

Dev server default URL (per `SocOps/Properties/launchSettings.json`): `http://localhost:5166`

## Coding Conventions

- C#: follow standard conventions (PascalCase public members, file-scoped namespaces if consistent with surrounding code).
- Keep changes **surgical**: don’t rename public APIs or restructure files unless requested.
- Don’t introduce new dependencies unless clearly needed and consistent with the repo.

## UI / Styling Conventions

This project uses **custom Tailwind-like utility classes** in `SocOps/wwwroot/css/app.css`.

- Compose existing utilities first (layout/spacing/typography/colors).
- If a new utility is truly needed, add it to `app.css` following existing patterns.
- Prefer CSS variables for themeable values.

See: `.github/instructions/css-utilities.instructions.md`

## State / Logic

- `BingoGameService` manages `GameState` and notifies UI via events.
- `BingoLogicService` contains game rules / bingo line logic.
- Keep UI components focused on rendering; keep logic in services/models.

## PR/Change Checklist

Before finishing a task:

- `dotnet build SocOps/SocOps.csproj` succeeds
- If tests exist: `dotnet test` succeeds
- No obvious analyzer warnings introduced (unused usings/variables)
