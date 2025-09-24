# EC2 REST Service: Pounds → Kilograms

## Run locally
```bash
npm install
npm start
# http://localhost:8080/convert?lbs=150
```

## API
GET `/convert?lbs=<number>`
- **200**: `{ "lbs": 150, "kg": 68.039, "formula": "kg = lbs * 0.45359237" }`
- **400**: missing/not-a-number
- **422**: negative or non-finite

## EC2 public endpoint
- `http://<PUBLIC_IP_OR_DNS>/convert?lbs=150`

## Screenshots to submit
- Successful curl
- Error codes (400 & 422)
- `systemctl status p1`
- Security Group rules
