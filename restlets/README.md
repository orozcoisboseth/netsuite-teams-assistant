## Sample RESTlet

The original implementation uses a centralized action-routing pattern.

Supported actions include:

- getData
- updateRecord
- getRecordPDF
- sendEmail
- approvePO
- cancelPO

```javascript
{
  "action": "approvePO",
  "poNumber": "PO-12345"
}
```
