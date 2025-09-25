# DESIGN — EC2 REST Service: Pounds → Kilograms

## 1) Goal & Requirements
Provide a tiny HTTP REST service that converts pounds (lbs) to kilograms (kg), deploy it on an AWS EC2 instance, and document how to test it remotely.

**Functional**
- `GET /convert?lbs=<number>` → JSON `{ lbs, kg, formula }`
- Round `kg` to **3 decimals** using factor `0.45359237`.

**Validation / Errors**
- **400 Bad Request** – missing `lbs` or not numeric.
- **422 Unprocessable Entity** – negative or non-finite (`±Inf/NaN`).

**Non-Functional**
- Runs persistently (auto-start and restart on failure).
- Publicly reachable for grading.
- Minimal cost (t*-micro instance).

---

## 2) Architecture & Tech Choices
- **Runtime:** Node.js + Express (small footprint, easy JSON).
- **Logging:** `morgan` HTTP access logs to stdout (view via `journalctl`).
- **Endpoint:** Single GET endpoint; simple query string avoids request body parsing.
- **Rationale:** Fast to implement, clear error handling, precise constant, trivial deploy on AL2.

