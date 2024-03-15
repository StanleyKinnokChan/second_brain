# Health checks

- Health check are separate from, but are used by records
- health checkers located globally, not only AWS!
- health checkers check every 30s
- check TCP, HTTP/HTTPS, HTTP/HTTPS with string matching
- 3 types:
    - endpoint
    - cloudwatch alarm
    - checks of checks
