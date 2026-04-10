# 🌱 Plant Manager

A C# console application for managing your houseplants. Track watering schedules, monitor plant health, import and export plant logs, and manage user accounts — all from the command line.

---

## Features

- **User Authentication** — Register and log in with hashed password storage (SHA-256)
- **Plant Management** — Add, remove, and view plants of different species
- **Health Tracking** — Plant health decays over time based on watering schedules and age
- **Watering System** — Water individual plants and receive dynamic feedback
- **Import / Export Logs** — Load and save plant data to and from `.txt` files
- **Persistent Storage** — Plant and user data saved locally between sessions

---

## Plant Species

| Species | Watering Interval | Health Decay Rate |
|---------|------------------|-------------------|
| Cactus  | Every 14 days    | 5 pts/day overdue |
| Fern    | Every 5 days     | 10 pts/day overdue |
| Flower  | Every 3 days     | 15 pts/day overdue |

Each species has unique care instructions and a calculated next watering date.

---

## Project Structure

```
PlantManager/
├── Models/
│   ├── Plant.cs           # Abstract base class for all plants
│   ├── Cactus.cs          # Cactus species implementation
│   ├── Fern.cs            # Fern species implementation
│   └── Flower.cs          # Flower species implementation
├── Services/
│   ├── PlantManager.cs    # Core plant operations (add, remove, water, import/export)
│   ├── Authorisation.cs   # User registration and login logic
│   ├── SecurityService.cs # Password hashing and verification
│   └── DataHandler.cs     # File I/O for user data persistence
├── Interfaces/
│   └── IUserIO.cs         # Abstraction for console I/O (enables testing)
└── Tests/
    ├── AddPlantTest/       # Unit tests for plant creation via PlantManager
    ├── RegisterTest/       # Unit tests for user registration and authentication
    └── RootCommandTests/   # Unit tests for watering, log import, and plant removal
```

---

## Getting Started

### Prerequisites

- [.NET Framework 4.7.2](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net472) or later
- Visual Studio 2019+ (recommended)

### Running the App

1. Clone the repository:
   ```bash
   git clone https://github.com/chanri0702-jpg/Profile-Repository.git
   ```
2. Open the `.sln` file in Visual Studio.
3. Build and run the project (`F5` or `Ctrl+F5`).

### Running Tests

The solution includes xUnit test projects. Run all tests via:

```bash
dotnet test
```

Or use the Test Explorer in Visual Studio.

---

## Data Storage

- **Plant data** is saved to `PlantStorage.txt` in your Documents folder under `PlantLogs/`
- **User data** is saved to `userData.txt` in the application directory
- Passwords are **never stored in plain text** — SHA-256 hashing is applied before saving

---

## Testing Approach

The project uses **xUnit** for unit testing with an `IUserIO` interface to mock console input/output, enabling fully automated tests without user interaction.

Key test coverage includes:
- Plant creation (valid species, boundary inputs)
- User registration (empty fields, duplicate usernames, valid credentials)
- Watering logic (valid and invalid plant indices)
- Log import (valid files, missing files)
- Plant removal (exact match, case-insensitive, not found)

---

## Author

**Chanri du Randt**  
Undergraduate Software Engineer — Belgium Campus ITVersity  
[LinkedIn](https://www.linkedin.com/in/chanri-du-randt-8b1359286/) | [GitHub](https://github.com/chanri0702-jpg/Profile-Repository)
