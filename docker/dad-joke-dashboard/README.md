# A multi-container application using Docker Compose - a dad joke dashboard where one container fetches jokes and another serves them.


A live dashboard with two containers:

┌─────────────────┐         ┌─────────────────┐
│     updater     │         │      nginx      │
│     (bash)      │         │                 │
│                 │         │                 │
│  fetch jokes    │         │   serve HTML    │
│  write HTML ────┼────────▶│                 │
└─────────────────┘         └─────────────────┘
         │                          │
         └──────── /html ───────────┘
              (shared volume)

* updater: Bash container that fetches dad jokes from an API every 30 seconds
* nginx: Serves the generated HTML page
* shared volume: Both containers access the same /html directory
