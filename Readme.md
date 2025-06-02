The issue is clear now: prometheus.yml is a directory (as indicated by d----- in the Mode column), but Docker expects it to be a file for mounting into the container.
1. Delete the directory (since it shouldn't be a folder):
```Remove-Item -Recurse -Force .\docker\prometheus\prometheus.yml```
2. Create a proper prometheus.yml file:
```New-Item -ItemType File -Path .\docker\prometheus\prometheus.yml```
3. Verify it's now a file:
```Get-Item .\docker\prometheus\prometheus.yml```
4. Restart Docker Compose:
```docker compose up -d```