# AI Security Auditor

An intelligent code analysis tool that leverages OpenAI's GPT models to automatically identify and explain security vulnerabilities in source code. Built with React, Node.js, and PostgreSQL.

## 🔍 Features

- **AI-Powered Analysis**: Uses GPT-3.5-turbo to perform comprehensive security audits
- **Multi-Language Support**: Analyzes JavaScript, TypeScript, Python, Java, PHP, C#, Ruby, Go, C++, and C
- **File Upload & Text Input**: Submit code via file upload or direct text input
- **Comprehensive Reports**: Detailed vulnerability reports with severity levels, descriptions, and fix recommendations
- **Persistent Storage**: PostgreSQL database stores all audit results
- **Real-time Statistics**: Track total analyses and vulnerabilities found
- **Modern UI**: Clean, responsive interface built with React and Tailwind CSS

## 🚀 Live Demo

[Add your deployed application URL here]

## 🛠️ Technology Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **shadcn/ui** component library
- **TanStack Query** for state management
- **Wouter** for routing
- **React Hook Form** with Zod validation

### Backend
- **Node.js** with Express
- **TypeScript** for type safety
- **Drizzle ORM** for database operations
- **PostgreSQL** for data persistence
- **OpenAI API** for AI-powered analysis
- **Multer** for file uploads

## 📋 Prerequisites

- Node.js 18+ 
- PostgreSQL database
- OpenAI API key

## ⚙️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ai-security-auditor.git
   cd ai-security-auditor
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```env
   DATABASE_URL=your_postgresql_connection_string
   OPENAI_API_KEY=your_openai_api_key
   ```

4. **Set up the database**
   ```bash
   npm run db:push
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```

The application will be available at `http://localhost:5000`

## 🔒 Security Analysis Features

### Vulnerability Detection
- **SQL Injection**: Identifies unsafe database queries
- **Cross-Site Scripting (XSS)**: Detects potential XSS vulnerabilities
- **Hardcoded Secrets**: Finds API keys and passwords in code
- **Input Validation**: Checks for insufficient input sanitization

### Analysis Options
Users can customize analysis by enabling/disabling specific vulnerability checks:
- SQL Injection Detection
- Hardcoded Secrets & API Keys
- Cross-Site Scripting (XSS)
- Input Validation Issues

### Severity Levels
- **Critical**: Immediate security risks requiring urgent attention
- **Medium**: Important vulnerabilities that should be addressed
- **Low**: Minor issues or potential improvements

## 📊 Sample Analysis Output

```json
{
  "securityScore": 6,
  "vulnerabilities": [
    {
      "id": "sql-injection-001",
      "title": "SQL Injection Vulnerability",
      "severity": "CRITICAL",
      "description": "Direct string concatenation in SQL query allows injection attacks",
      "code": "SELECT * FROM users WHERE username = '" + username + "'",
      "lineNumber": 15,
      "recommendation": "Use parameterized queries or prepared statements",
      "fixExample": "SELECT * FROM users WHERE username = ?"
    }
  ],
  "summary": {
    "critical": 1,
    "medium": 0,
    "low": 2
  }
}
```

## 🗂️ Project Structure

```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Page components
│   │   ├── hooks/          # Custom React hooks
│   │   └── lib/            # Utility functions
├── server/                 # Express backend
│   ├── index.ts           # Server entry point
│   ├── routes.ts          # API routes
│   ├── storage.ts         # Database operations
│   ├── openai.ts          # OpenAI integration
│   └── db.ts              # Database configuration
├── shared/                 # Shared types and schemas
│   └── schema.ts          # Drizzle database schema
└── package.json
```

## 🔧 API Endpoints

### POST `/api/analyze`
Analyze code via text input
```json
{
  "code": "string",
  "language": "string",
  "filename": "string (optional)",
  "analysisOptions": {
    "checkSQLInjection": true,
    "checkHardcodedSecrets": true,
    "checkXSS": true,
    "checkInputValidation": true
  }
}
```

### POST `/api/analyze-file`
Analyze code via file upload
- Supports: `.js`, `.ts`, `.py`, `.java`, `.php`, `.cs`, `.rb`, `.go`, `.cpp`, `.c`
- Max file size: 5MB

### GET `/api/stats`
Get analysis statistics
```json
{
  "totalAnalyses": 42,
  "vulnerabilitiesFound": 156
}
```

### GET `/api/audit/:id`
Retrieve specific audit results

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for providing the GPT models
- The open-source community for the excellent tools and libraries used in this project

## 📞 Support

If you encounter any issues or have questions, please [open an issue](https://github.com/yourusername/ai-security-auditor/issues) on GitHub.

---

**⚠️ Disclaimer**: This tool is designed to assist in identifying potential security vulnerabilities but should not be the only security measure. Always perform comprehensive security reviews and testing before deploying code to production.
