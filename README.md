# 🐍 Code Explainer and Fixer

An AI-powered tool that helps students and early-career developers understand, debug, and improve their Python code. Get instant feedback with high-level summaries, line-by-line explanations, bug detection, and improved code versions.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.109.0-green.svg)
![React](https://img.shields.io/badge/React-18+-61DAFB.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## ✨ Features

- **📝 High-Level Summary** - Get a concise explanation of what your code does
- **🔍 Line-by-Line Explanations** - Understand each significant line with beginner-friendly language
- **🐛 Bug Detection** - Identify syntax errors, runtime errors, and logical bugs
- **⚡ Performance Analysis** - Detect inefficiencies and bad coding practices
- **✅ Code Improvements** - Receive an improved version with best practices applied
- **🎓 Learning Aids** - Concept highlighting and educational tips (optional)
- **📊 Visual Diff** - Side-by-side comparison of original vs improved code (optional)
- **🎯 Demo Mode** - Fast, cached results perfect for presentations

## 🚀 Quick Start

### Prerequisites

- **Python 3.10+**
- **Node.js 16+** (for frontend)
- **OpenAI API Key** ([Get one here](https://platform.openai.com/api-keys))

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/code-explainer-fixer.git
   cd code-explainer-fixer/backend
   ```

2. **Create and activate virtual environment**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` and add your OpenAI API key:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

5. **Run the backend server**
   ```bash
   uvicorn app.main:app --reload
   ```
   
   The API will be available at `http://localhost:8000`
   
   API documentation: `http://localhost:8000/docs`

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd ../frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure API endpoint**
   ```bash
   cp .env.example .env.local
   ```
   
   Edit `.env.local`:
   ```env
   VITE_API_URL=http://localhost:8000
   ```

4. **Run the development server**
   ```bash
   npm run dev
   ```
   
   The app will be available at `http://localhost:5173`

## 📖 Usage

### Basic Analysis

1. Open the web application
2. Paste your Python code into the editor
3. Click "Analyze Code"
4. View the four analysis sections:
   - Summary
   - Line-by-Line Explanations
   - Issues Detected
   - Improved Code

### Using Sample Code

Click the "Load Sample" dropdown to try pre-loaded examples:
- Buggy code with errors
- Inefficient code with performance issues
- Clean code following best practices

### API Usage

```bash
curl -X POST "http://localhost:8000/api/analyze" \
  -H "Content-Type: application/json" \
  -d '{
    "code": "def greet(name):\n    print(\"Hello \" + name)",
    "options": {
      "include_summary": true,
      "include_explanation": true,
      "include_issues": true,
      "include_improved": true
    }
  }'
```

## 🏗️ Project Structure

```
code-explainer-fixer/
├── backend/                    # FastAPI backend
│   ├── app/
│   │   ├── main.py            # FastAPI application
│   │   ├── config.py          # Configuration & feature flags
│   │   ├── models/            # Pydantic data models
│   │   │   └── schemas.py
│   │   ├── services/          # Business logic
│   │   │   ├── validator.py
│   │   │   ├── ai_service.py
│   │   │   └── analyzer.py
│   │   ├── api/               # API routes
│   │   │   └── routes.py
│   │   └── data/              # Sample code
│   │       └── samples.py
│   ├── tests/                 # Test files
│   ├── requirements.txt       # Python dependencies
│   └── .env.example          # Environment template
│
├── frontend/                  # React frontend
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── services/         # API client
│   │   ├── App.tsx           # Main application
│   │   └── main.tsx          # Entry point
│   ├── package.json          # Node dependencies
│   └── .env.example         # Environment template
│
└── README.md                 # This file
```

## 🧪 Testing

### Backend Tests

```bash
cd backend

# Run all tests
pytest

# Run with coverage
pytest --cov=app tests/

# Run specific test file
pytest tests/test_models.py -v

# Run property-based tests
pytest tests/test_validation_properties.py -v
```

### Frontend Tests

```bash
cd frontend

# Run tests
npm test

# Run with coverage
npm run test:coverage
```

## ⚙️ Configuration

### Feature Flags

Enable/disable optional features via environment variables in `backend/.env`:

```env
# Optional Features (set to "true" or "false")
ENABLE_DIFF_VIEW=false              # Visual diff comparison
ENABLE_LEARNING_AIDS=false          # Concept highlighting & tips
ENABLE_CUSTOMIZATION=false          # Explanation depth control
ENABLE_EXPORT=false                 # Export to PDF/Markdown/HTML
ENABLE_CONFIDENCE=false             # Confidence indicators
ENABLE_PEP8_CHECK=false            # PEP 8 style checking
ENABLE_PERFORMANCE_ANALYSIS=false   # Performance optimization suggestions
ENABLE_DEMO_MODE=true              # Fast cached results for demos
```

### Analysis Constraints

- **Maximum code length**: 500 lines
- **Analysis timeout**: 30 seconds
- **Supported language**: Python only

## 🎯 Demo Mode

Perfect for presentations and hackathons:

1. Set `ENABLE_DEMO_MODE=true` in `.env`
2. Use pre-loaded sample code for instant results
3. Cached responses ensure fast, consistent output
4. Enhanced visual emphasis for screen sharing

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 for Python code
- Use TypeScript for frontend code
- Write tests for new features
- Update documentation as needed

## 📝 API Documentation

### Endpoints

#### `POST /api/analyze`

Analyze Python code and return comprehensive results.

**Request Body:**
```json
{
  "code": "string (required)",
  "options": {
    "include_summary": true,
    "include_explanation": true,
    "include_issues": true,
    "include_improved": true,
    "explanation_depth": "standard",
    "demo_mode": false
  }
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "summary": "High-level summary...",
    "line_by_line": [...],
    "issues": [...],
    "improved_code": "...",
    "original_code": "..."
  },
  "error": null
}
```

#### `GET /api/samples`

Get pre-loaded sample code snippets.

**Response:**
```json
{
  "samples": [
    {
      "id": "sample1",
      "title": "Hello World",
      "description": "A simple program",
      "code": "print('Hello')",
      "category": "clean"
    }
  ]
}
```

Full API documentation available at `http://localhost:8000/docs` when running the backend.

## 🛠️ Tech Stack

### Backend
- **FastAPI** - Modern Python web framework
- **OpenAI API** - GPT-3.5/GPT-4 for code analysis
- **Pydantic** - Data validation and settings management
- **Pytest** - Testing framework
- **Hypothesis** - Property-based testing

### Frontend
- **React** - UI library
- **TypeScript** - Type-safe JavaScript
- **Vite** - Build tool and dev server
- **Monaco Editor** - Code editor with syntax highlighting
- **Tailwind CSS** - Utility-first CSS framework
- **Axios** - HTTP client

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for providing the GPT API
- FastAPI for the excellent web framework
- The Python and React communities

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Built with ❤️ for students and developers learning Python**
