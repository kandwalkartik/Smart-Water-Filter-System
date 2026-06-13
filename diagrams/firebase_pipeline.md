# Firebase Pipeline

Label: Implemented architecture, dashboard presentation documented conceptually

```mermaid
flowchart LR
    A["ESP8266 NodeMCU"] --> B["Wi-Fi"]
    B --> C["Firebase Realtime Database"]
    C --> D["Flutter App"]
    D --> E["Home Screen"]
    D --> F["Analytics Screen"]
    D --> G["Filters Screen"]

    A -. "Publishes" .-> H["TDS"]
    A -. "Publishes" .-> I["Mode"]
    A -. "Publishes" .-> J["Active Path"]
    A -. "Publishes" .-> K["Runtime Data"]
    A -. "Publishes" .-> L["Filter Usage"]
```

## Scope Boundary

The project uses Firebase and Flutter. No additional cloud analytics platform is claimed.
