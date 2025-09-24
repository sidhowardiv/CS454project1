# DESIGN

## Stack
Node.js + Express with `morgan` for access logs. Lightweight JSON server suitable for a single endpoint.

## API
- `GET /convert?lbs=<number>`
- Uses precise factor `0.45359237`; returns 3-decimal rounded result and echoes the input.
- Example: `150 lbs -> 68.039 kg`.

## Validation & Errors
- **400** when param missing or not numeric.
- **422** when negative or non-finite (±Inf/NaN).

## Deployment
- Run under `systemd` as `p1` service with `Restart=always` so it auto-starts on boot and restarts on crash.
- Optional NGINX reverse proxy to expose on port 80.

## Security
- Security Group: allow SSH (22) only from your IP; allow HTTP (80) or service port (8080) for public access.
- Run as `ec2-user` (non-root).

## Testing
- `curl` happy path and error cases.
- Inspect logs with `journalctl -u p1`.

## Cleanup
- Terminate EC2 instance, delete unused Security Group and Key Pair.
