
# **API Documentation: Create Document from Template**

## **Endpoint**

**URL**: `TBC`  
**Method**: `POST`  

## **Description**

This endpoint allows you to create a document from a specified template by providing relevant field data, signatories, and additional metadata.

---

## **Headers**

| Key             | Value                       |
|------------------|-----------------------------|
| `Content-Type`   | `application/json`          |
| `Authorization`  | `Bearer <your-access-token>` |

---

## **Request Body**

The request body should be a JSON object with the following fields:

### **1. template**
- **Type**: `string`
- **Description**: The unique identifier of the template to use for document creation.
- **Example**: `"13891pUEAUsWlpAFDMMxySWfftKGmn0xPYgTw6ocJWNc"`

---

### **2. template_name**
- **Type**: `string`
- **Description**: The name of the templatized document after creation.
- **Example**: `"lenka.stefkovicova_01-09-25_Mandate_Agreement_VL-SK_1.0"`

---

### **3. fields**
- **Type**: `array`
- **Description**: A list of key-value pairs for populating the fields in the document (e.g. field documentDate will populate {{documentDate}} placeholder).
- **Structure**:
  ```json
  [
      {
          "field": "documentDate",
          "value": "9/21/2025"
      },
      {
          "field": "repPartyID",
          "value": "46584838"
      }
  ]
  ```

---

### **4. signatories**
- **Type**: `array`
- **Description**: A list of signatories associated with the document. "position" and "company" is optional.
- **Structure**:
  ```json
  [
      {
          "email": "lenka.stefkovicova@vacuumlabs.com",
          "name": "miro skovajsa",
          "position": "CEO",
          "company": "vacuumlabs s.r.o."
      },
      {
          "email": "lenka.stefkovicova3@gmail.com",
          "name": "Lenka",
          "company": "Lenka Štefkovičová"
      }
  ]
  ```

---

### **5. request_signatures**
- **Type**: `boolean`
- **Description**: Whether to automatically request digital signatures from the specified signatories.
- **Example**: `false`

---

### **6. spadog_user**
- **Type**: `string`
- **Description**: User identifier for authentication within the Sparring Dog.
- **Example**: `"google-oauth2|116385764127171084425"`

---

### **7. project_token**
- **Type**: `string`
- **Description**: Token identifying the project associated with this document creation.
- **Example**: `"ec1831b8-1c71-4779-8bf8-275623398567"`

---

## **Example cURL Request**

```bash
curl -X POST https://api.example.com/v1/documents/create \
-H "Authorization: Bearer <your-access-token>" \
-H "Content-Type: application/json" \
-d '[
    {
        "template": "13891pUEAUsWlpAFDMMxySWfftKGmn0xPYgTw6ocJWNc",
        "template_name": "lenka.stefkovicova_01-09-25_Mandate_Agreement_VL-SK_1.0",
        "fields": [
            {"field": "documentDate", "value": "9/21/2025"},
            {"field": "repPartyID", "value": "46584838"}
        ],
        "signatories": [
            {"email": "lenka.stefkovicova@vacuumlabs.com", "name": "miro skovajsa", "position": "CEO", "company": "vacuumlabs s.r.o."},
            {"email": "lenka.stefkovicova3@gmail.com", "name": "Lenka", "company": "Lenka Štefkovičová"}
        ],
        "request_signatures": false,
        "spadog_user": "google-oauth2|116385764127171084425",
        "project_token": "ec1831b8-1c71-4779-8bf8-275623398567"
    }
]'
```

--- 
