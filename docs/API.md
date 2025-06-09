# API Documentation

## Base URL
```
http://localhost:5000/api
```

## Authentication
Currently, no authentication is required for API endpoints.

## Endpoints

### 1. Analyze Code (Text Input)

**POST** `/analyze`

Analyzes code provided as text input.

#### Request Body
```json
{
  "code": "string (required) - The source code to analyze",
  "language": "string (required) - Programming language",
  "filename": "string (optional) - Name of the file",
  "analysisOptions": {
    "checkSQLInjection": "boolean (default: true)",
    "checkHardcodedSecrets": "boolean (default: true)", 
    "checkXSS": "boolean (default: true)",
    "checkInputValidation": "boolean (default: true)"
  }
}
```

#### Response
```json
{
  "auditId": 123,
  "securityScore": 7,
  "vulnerabilities": [
    {
      "id": "unique-vulnerability-id",
      "title": "Vulnerability Title",
      "severity": "CRITICAL | MEDIUM | LOW",
      "description": "Detailed description",
      "code": "Vulnerable code snippet",
      "lineNumber": 15,
      "recommendation": "How to fix it",
      "fixExample": "Corrected code example"
    }
  ],
  "summary": {
    "critical": 1,
    "medium": 2,
    "low": 0
  }
}
```

#### Example
```bash
curl -X POST http://localhost:5000/api/analyze \
  -H "Content-Type: application/json" \
  -d '{
    "code": "SELECT * FROM users WHERE id = '\''" + userId + "'\''",
    "language": "JavaScript",
    "analysisOptions": {
      "checkSQLInjection": true,
      "checkHardcodedSecrets": false,
      "checkXSS": true,
      "checkInputValidation": true
    }
  }'
```

### 2. Analyze File Upload

**POST** `/analyze-file`

Analyzes code from an uploaded file.

#### Request
- **Content-Type**: `multipart/form-data`
- **Form Fields**:
  - `file`: The code file to analyze
  - `checkSQLInjection`: "true" | "false"
  - `checkHardcodedSecrets`: "true" | "false"
  - `checkXSS`: "true" | "false"
  - `checkInputValidation`: "true" | "false"

#### Supported File Types
- `.js` - JavaScript
- `.jsx` - JavaScript React
- `.ts` - TypeScript
- `.tsx` - TypeScript React
- `.py` - Python
- `.java` - Java
- `.php` - PHP
- `.cs` - C#
- `.rb` - Ruby
- `.go` - Go
- `.cpp` - C++
- `.c` - C

#### File Size Limit
Maximum file size: 5MB

#### Response
Same as `/analyze` endpoint, with additional fields:
```json
{
  "auditId": 123,
  "filename": "example.js",
  "language": "JavaScript",
  "securityScore": 7,
  "vulnerabilities": [...],
  "summary": {...}
}
```

#### Example
```bash
curl -X POST http://localhost:5000/api/analyze-file \
  -F "file=@example.js" \
  -F "checkSQLInjection=true" \
  -F "checkHardcodedSecrets=true" \
  -F "checkXSS=true" \
  -F "checkInputValidation=true"
```

### 3. Get Analysis Statistics

**GET** `/stats`

Returns overall statistics about analyses performed.

#### Response
```json
{
  "totalAnalyses": 156,
  "vulnerabilitiesFound": 432
}
```

#### Example
```bash
curl http://localhost:5000/api/stats
```

### 4. Get Audit by ID

**GET** `/audit/:id`

Retrieves a specific security audit by its ID.

#### Parameters
- `id` (path parameter): The audit ID

#### Response
```json
{
  "id": 123,
  "code": "Original code that was analyzed",
  "language": "JavaScript",
  "filename": "example.js",
  "analysisOptions": {
    "checkSQLInjection": true,
    "checkHardcodedSecrets": true,
    "checkXSS": true,
    "checkInputValidation": true
  },
  "securityScore": 7,
  "vulnerabilities": [...],
  "createdAt": "2025-06-09T18:30:00.000Z"
}
```

#### Example
```bash
curl http://localhost:5000/api/audit/123
```

## Error Responses

### 400 Bad Request
```json
{
  "message": "Invalid request data",
  "errors": [
    {
      "field": "code",
      "message": "Code is required"
    }
  ]
}
```

### 404 Not Found
```json
{
  "message": "Audit not found"
}
```

### 429 Too Many Requests
```json
{
  "message": "You exceeded your current quota, please check your plan and billing details."
}
```

### 500 Internal Server Error
```json
{
  "message": "Analysis failed"
}
```

## Rate Limiting

Currently, no rate limiting is implemented. However, be mindful of OpenAI API rate limits and quotas.

## Data Types

### Vulnerability Object
```typescript
interface Vulnerability {
  id: string;
  title: string;
  severity: "CRITICAL" | "MEDIUM" | "LOW";
  description: string;
  code: string;
  lineNumber?: number;
  recommendation: string;
  fixExample?: string;
}
```

### Analysis Options
```typescript
interface AnalysisOptions {
  checkSQLInjection: boolean;
  checkHardcodedSecrets: boolean;
  checkXSS: boolean;
  checkInputValidation: boolean;
}
```

### Security Report
```typescript
interface SecurityReport {
  securityScore: number; // 0-10
  vulnerabilities: Vulnerability[];
  summary: {
    critical: number;
    medium: number;
    low: number;
  };
}
```
