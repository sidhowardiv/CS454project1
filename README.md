# lbs-to-kg-converter
Project 1 CS 454

A simple Node.js web service that converts pounds (lbs) to kilograms (kg).  
Accepts a `lbs` query parameter and returns JSON with the conversion result.

---

## Install dependencies
npm install

## Start the server
node server.js

## Test with curl
curl http://18.222.143.237:8080/convert?lbs=150

---

## Test Cases

curl http://18.222.143.237:8080/convert?lbs=0
-> {"lbs":0,"kg":0,"formula":"kg = lbs * 0.45359237"}

curl http://18.222.143.237:8080/convert?lbs=0.1
-> {"lbs":0.1,"kg":0.045,"formula":"kg = lbs * 0.45359237"}

curl http://18.222.143.237:8080/convert?lbs=-5
->422 error

curl http://18.222.143.237:8080/convert
-> 400 error

curl http://18.222.143.237:8080/convert?lbs=NaN
-> 400 error

---

## Screenshots

### Successful curl requests


### Error cases


---

## Public Endpoint & Security Group

**Public Endpoint:**  
http://18.222.143.237:8080

**Security Group Summary:**

Protocol | Port | Source    | Purpose
---------|------|-----------|---------------------------
TCP      | 22   | My IP     | SSH access (login)
TCP      | 8080 | 0.0.0.0/0 | REST API testing (Node.js)
