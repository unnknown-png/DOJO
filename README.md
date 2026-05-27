# DOJO (Daily Objectives Journey On) 🚀

A cross-platform productivity app that combines planning, time management, and gamification. DOJO helps users plan goals and tasks, track progress, and stay motivated through levels and rewards.

This repository contains a .NET MAUI desktop app with a clean 3-layer architecture (Presentation, BLL, DAL) and a PostgreSQL database.

## Highlights ✨

- Goal planning with start and end times, priority, and progress tracking.
- Task management with priorities, completion tracking, and attachments.
- Pomodoro sessions with short and long break cycles.
- Gamification layer with XP, levels, and streak tracking.
- Productivity and statistics dashboards.
- Local session persistence (SecureStorage with Preferences fallback).

## Architecture 🧱

DOJO is organized into three layers:

- Presentation (Presentation): .NET MAUI UI, MVVM ViewModels, Shell navigation, and DI setup.
- BLL (BLL): business logic services (users, tasks, goals, pomodoro, experience, sessions).
- DAL (DAL): EF Core DbContext and entity models for PostgreSQL.

Key entry points:

- `dojo/Presentation/MauiProgram.cs` registers DI services, DbContext, and Serilog logging.
- `dojo/DAL/DojoDbContext.cs` maps entities to database tables and applies conventions.

## Tech Stack 🛠️

- .NET MAUI (UI)
- C# / MVVM
- Entity Framework Core
- PostgreSQL
- Serilog (file and debug logging)
- xUnit, Moq, FluentAssertions (tests)

## Data Model (Core Entities) 🧩

- User: email, password hash, XP, level, streaks, created date
- Goal: time range, progress, priority, completion state
- ToDoTask: task description, due date, priority, completion state
- Pomodoro: user session logs, duration, work cycles
- Attachment: file metadata linked to tasks or goals

Relationships are defined in `dojo/DAL/DojoDbContext.cs`.

## Project Structure 🗂️

```
DOJO/
  DB/                      Database SQL scripts
  Documents/               Requirements, diagrams, and wireframes
  dojo/
    Presentation/          MAUI UI (Views, ViewModels, resources)
    BLL/                   Business logic services
    DAL/                   EF Core models and DbContext
    BLL.Tests/             Unit tests for business logic
    DAL.Tests/             Unit tests for data layer
```

## Documentation 📚

Project documents and diagrams are available in the `Documents/` folder:

- `Documents/DOJO.pdf` - full project documentation
- `Documents/Description/functional_req.pdf`
- `Documents/Description/non_functional_req.pdf`
- `Documents/Data_Base/dataBase_description.pdf`
- `Documents/Data_Base/ER_diagram.png`
- `Documents/Data_Base/UML_diagram.png`
- `Documents/Usecase/Student_usecase.png`
- `Documents/Usecase/Proff_usecase.png`
- `Documents/Usecase/Own_usecase.png`
- `Documents/Usecase/Roles.pdf`
- `Documents/Wireframe/Wireframes.pdf`

## Getting Started 🧭

### Prerequisites ✅

- .NET SDK 9.x (pinned by `dojo/global.json`)
- .NET MAUI workload (`dotnet workload install maui`)
- PostgreSQL (local or remote)
- Xcode (macOS only, required for MacCatalyst builds)

### Database Setup 🗄️

Create a PostgreSQL database and apply the script:

```
DB/dojo.sql
```

### Configuration ⚙️

The app currently uses a connection string in `dojo/Presentation/MauiProgram.cs`:

```
Host=localhost;Database=dojo;Username=postgres;Password=YOUR_PASSWORD
```

Update it to match your local database. For production, move secrets into user secrets or environment variables.

### Build 🏗️

```bash
dotnet restore
dotnet build dojo/dojo.sln
```

### Run (macOS, MacCatalyst) 🍎

```bash
dotnet build -t:Run -f net9.0-maccatalyst18.0 dojo/Presentation/Presentation.csproj
```

### Run (Windows) 🪟

```bash
dotnet build -t:Run -f net9.0-windows10.0.19041.0 dojo/Presentation/Presentation.csproj
```

### Tests 🧪

```bash
dotnet test dojo/BLL.Tests/BLL.Tests.csproj
dotnet test dojo/DAL.Tests/DAL.Tests.csproj
```

## Logging 🧾

Serilog writes logs to an app data folder (DojoLogs) and to the debug output. See `dojo/Presentation/MauiProgram.cs` for configuration details.

## Team 👥

- Vladyslav Kovalchuk - Frontend Developer, Project Manager
- Solomiia Chvartkovska - Frontend Developer, UI/UX Design
- Anna Dzhavala - Backend Developer
- Andrii Kakhnovets - Backend Developer

## Developed with .NET MAUI and PostgreSQL by the DOJO Team