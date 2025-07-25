# README.md: Android Auto EV Dashboard App

This repository contains the source code for an Android application designed to display car-related information, specifically for Electric Vehicles (EVs), on the infotainment system of a car via Android Auto. The application will provide a dashboard view of key EV metrics such as State of Charge (SoC).

## Co-development Methodology

This project is developed using the AGILE-AI Protocol, a co-development methodology that strictly defines the interaction and workflow between a human developer and an AI agent. The AI agent adheres to a Test-Driven Development (TDD) cycle and a structured debugging protocol to ensure code quality, reliability, and maintainability.

For detailed guidelines on the co-development process, refer to the `SPEC.md` document.

## Project Structure (Planned)

```
. (project root)
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── AndroidManifest.xml
│   │   │   ├── java/ (or kotlin/)
│   │   │   │   └── com/example/aacarinfo/
│   │   │   │       ├── MainActivity.kt (or .java)
│   │   │   │       ├── auto/
│   │   │   │       │   └── EvDashboardService.kt (or .java)
│   │   │   │       └── data/
│   │   │   │           └── CarInfoRepository.kt (or .java)
│   │   └── test/
│   │       └── java/ (or kotlin/)
│   │           └── com/example/aacarinfo/
│   │               └── unit_tests/
│   │                   └── EvDashboardServiceTest.kt (or .java)
│   └── build.gradle
├── gradle/
├── .gitignore
├── SPEC.md
├── README.md
├── DEBUGGING.md
├── INSTRUCTIONS.md
├── PLAN.md
└── build.gradle (project level)
```

## Getting Started

Detailed instructions on setting up the development environment and running the application will be provided in `INSTRUCTIONS.md`.

## Debugging

For information on debugging procedures and protocols, please refer to `DEBUGGING.md`.

## Current Development Plan

The current development roadmap and planned features are outlined in `PLAN.md`.

## Contributing

Contributions are welcome! Please adhere to the AGILE-AI Protocol and the guidelines outlined in `SPEC.md`.
