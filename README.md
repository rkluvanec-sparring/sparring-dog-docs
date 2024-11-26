
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
- **Example**: `"g7df8gsdf465g4df8g7dfgsdfg7sdf8gdsf5fd4g"`

---

### **2. template_name**
- **Type**: `string`
- **Description**: The name of the templatized document after creation.
- **Example**: `"Mandate agreement - John Doe - 2024-04-10"`

---

### **3. fields**
- **Type**: `array`
- **Description**: A list of key-value pairs for populating the fields in the document (e.g. field documentDate will populate {{documentDate}} placeholder).
- **Structure**:
  ```json
  [
      {
          "field": "documentDate",
          "value": "10.04.2024"
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
          "email": "jane.doe@company.com",
          "name": "Jane Doe",
          "position": "CEO",
          "company": "Company Ltd."
      },
      {
          "email": "john.doe@gmail.com",
          "name": "John Doe",
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
- **Example**: `"15756496-75d5-4769-95fd-bc9ca0d137a5"`

---

### **7. project_token**
- **Type**: `string`
- **Description**: Token identifying the project associated with this document creation.
- **Example**: `"aa60754b-9ed1-4cd2-9047-12399b0637ee"`

---

## **Example cURL Request**

```bash
curl -X POST https://api.example.com/v1/documents/create \
-H "Authorization: Bearer <your-access-token>" \
-H "Content-Type: application/json" \
-d '[
    {
        "template": "g7df8gsdf465g4df8g7dfgsdfg7sdf8gdsf5fd4g",
        "template_name": "Mandate agreement - John Doe - 2024-04-10",
        "fields": [
            {"field": "documentDate", "value": "10.4.2024"},
            {"field": "repPartyID", "value": "46584838"}
        ],
        "signatories": [
            {"email": "jane.doe@company.com", "name": "Jane Doe", "position": "CEO", "company": "Company Ltd"},
            {"email": "john.doe@gmail.com", "name": "John Doe"}
        ],
        "request_signatures": false,
        "spadog_user": "15756496-75d5-4769-95fd-bc9ca0d137a5",
        "project_token": "aa60754b-9ed1-4cd2-9047-12399b0637ee"
    }
]'
```

--- 
