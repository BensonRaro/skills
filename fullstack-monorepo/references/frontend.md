# Frontend Reference

Frontend handles presentation, interaction, client state, API consumption, UX validation, accessibility, and loading/empty/error states.

Prefer feature organization:
```text
features/
├── admissions/
├── students/
├── teachers/
└── payments/
```

Keep feature components close to their feature. Use `components/ui/` for primitives and `components/globals/` for genuinely cross-feature application components.

Data flow:
```text
UI → hook/query → API client → backend
```

Centralize API URL, credentials, common headers, auth behavior, and error normalization.

Do not scatter raw API calls throughout presentational components.
