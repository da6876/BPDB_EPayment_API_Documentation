# ⚡ BPDB E-Payment API Documentation (UAT)

---

## 🌐 Base URL (UAT)

```
http://192.168.20.21/epay_api/uat/v1/
```
| `API User ID`   | ************ |
| `API Password`  | ************ |

---

# 1️⃣ Bill Query API

## 📌 Endpoint
```
POST /Payment_Gateway.php
```

## 📝 Description
Fetch bill information for a specific consumer account and billing cycle.

---

## 📥 Request Parameters

| Parameter        | Type   | Required | Description |
|------------------|--------|----------|-------------|
| `org_code`       | string | ✅ Yes   | Organization code (`BPDB`) |
| `acc_num`        | string | ✅ Yes   | Consumer Account Number |
| `billcycle`      | string | ✅ Yes   | Billing cycle format: `YYYYMM` |
| `pc_code`        | string | ✅ Yes   | Payment Center Code |
| `pc_br_code`     | string | ✅ Yes   | Payment Center Branch Code |
| `customer_code`  | string | ✅ Yes   | API User ID |
| `password`       | string | ✅ Yes   | API Password |
| `channel_type`   | string | ✅ Yes   | Channel Type (Provided by SRL) |
| `v`              | string | ✅ Yes   | API Version (`1`) |
| `format`         | string | ✅ Yes   | Response format (`json`) |

---

## 🔍 Sample Request

```http
POST /Payment_Gateway.php

org_code=BPDB
&acc_num=71816715
&billcycle=202602
&pc_code=01
&pc_br_code=100
&customer_code=Dbbl@Test
&password=Dbbl@Test1234
&channel_type=1
&v=1
&format=json
```

---

# 2️⃣ Bill Payment API

## 📌 Endpoint
```
POST /Payment_Gateway.php
```

## 📝 Description
Submit payment for a specific bill.

---

## 📥 Request Parameters

| Parameter        | Type   | Required | Description |
|------------------|--------|----------|-------------|
| `acc_num`        | string | ✅ Yes   | Consumer Account Number |
| `pc_code`        | string | ✅ Yes   | Payment Center Code |
| `trns_id`        | string | ✅ Yes   | Unique Transaction ID |
| `req_id`         | string | ✅ Yes   | Unique Request ID |
| `pay_date`       | string | ✅ Yes   | Payment Date (`DD/MM/YYYY`) |
| `customer_code`  | string | ✅ Yes   | API User ID |
| `password`       | string | ✅ Yes   | API Password |
| `channel_type`   | string | ✅ Yes   | Channel Type |
| `v`              | string | ✅ Yes   | API Version (`1`) |
| `format`         | string | ✅ Yes   | Response format (`json`) |

---

## 💳 Sample Payment Request

```http
POST /Payment_Gateway.php

acc_num=71816715
&pc_code=01
&trns_id=BAYAAAAAAAA
&req_id=MBP10000000058046
&pay_date=03/03/2026
&customer_code=Dbbl@Test
&password=Dbbl@Test1234
&channel_type=1
&v=1
&format=json
```

---

# 3️⃣ Payment Status Check API

## 📌 Endpoint
```
POST http://118.67.219.193/epay_dbbl/status_check.php
```

## 📝 Description
Check the status of a previously submitted payment request.

---

## 📥 Request Parameters

| Parameter   | Type   | Required | Description |
|------------|--------|----------|-------------|
| `org_code` | string | ✅ Yes   | Organization Code (`BPDB`) |
| `acc_num`  | string | ✅ Yes   | Consumer Account Number |
| `req_id`   | string | ✅ Yes   | Request ID used during payment |
| `v`        | string | ✅ Yes   | API Version (`1`) |
| `format`   | string | ✅ Yes   | Response format (`json`) |

---

## 🔎 Sample Status Request

```http
POST /status_check.php

org_code=BPDB
&acc_num=37230632
&req_id=MBP10000000058031
&v=1
&format=json
```

---

# 📦 Response Format

All APIs return responses in **JSON format**.

### ✅ Successful Response Example

```json
{
  "status": "SUCCESS",
  "message": "Payment completed successfully",
  "data": {
    "acc_num": "71816715",
    "amount": "1500.00",
    "transaction_id": "BAYAAAAAAAA"
  }
}
```

### ❌ Failed Response Example

```json
{
  "status": "FAILED",
  "message": "Invalid account number",
  "data": {}
}
```

---

# 🔐 Security & Best Practices

- 🔒 Keep `customer_code` and `password` confidential.
- 🔁 Ensure every `trns_id` and `req_id` is **unique**.
- 🌐 Use **HTTPS** in production environment.
- 🧾 Log all request and response data for reconciliation.
- ⏱ Implement timeout and retry handling carefully.

---

# 📌 Version Information

| Field | Value |
|-------|-------|
| API Version | `v=1` |
| Format | `json` |
| Environment | UAT |

---

## 📞 Support

For technical support or integration issues, please contact the API provider.

---

**End of Document**
