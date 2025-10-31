# AI Data Analyst 🤖📊

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)
[![GitHub](https://img.shields.io/badge/GitHub-heyitsgautham-181717?style=for-the-badge&logo=github)](https://github.com/heyitsgautham/data-analyst)

An intelligent data analysis system that combines web scraping, multi-format data extraction, and AI-powered analysis to answer complex data questions automatically. 🚀✨

## ✨ Features Included

### 📥 Multi-Source Data Ingestion
- 🌐 Web scraping with Playwright (JavaScript-rendered pages)
- 📋 HTML table extraction
- 📄 PDF data extraction (text and tables)
- 🖼️ Image OCR (extract data from screenshots/charts)
- 📊 CSV, JSON, Excel, SQL file processing
- 📦 Archive support (ZIP, TAR, TAR.GZ)

### 🧠 Intelligent Data Processing
- 🔢 Automatic numeric field detection and cleaning
- 💰 Currency, percentage, and scientific notation handling
- 🔗 Multi-table relationship detection
- 🗃️ Database query generation (DuckDB)
- 📅 Datetime parsing and standardization

### 🤖 AI-Powered Analysis
- 🎯 Multiple LLM support (GPT, Claude, Gemini, Grok)
- 📝 Task breakdown and execution planning
- 💬 Natural language question answering
- ⚙️ Automatic code generation for data analysis
- 🔄 Error recovery and retry mechanisms

### 🚀 Advanced Features
- 🧹 Automatic file cleanup after processing
- 📂 Support for multiple concurrent files
- 🛡️ Comprehensive error handling
- 📊 Progress tracking and detailed logging

## 🚀 How to Use It

### 📋 Prerequisites
- 🐍 Python 3.11+
- 🐳 Docker (optional)

### 💻 Installation

1. **📥 Clone the repository**
```bash
git clone https://github.com/heyitsgautham/data-analyst.git
cd dataanalyst
```

2. **📦 Install dependencies**
```bash
pip install -r requirements.txt
playwright install
```

3. **🔐 Set up environment variables**
Create a `.env` file with your API keys:
```env
API_KEY=your_openai_api_key
CLAUDE_API_KEY=your_claude_api_key
gemini_api=your_gemini_api_key
gemini_api_2=your_backup_gemini_key
grok_api=your_grok_api_key
OCR_API_KEY=your_ocr_space_key
```

4. **▶️ Run the application**
```bash
uvicorn app:app --host 0.0.0.0 --port 8000
```

### 🐳 Using Docker

```bash
docker build -t ai-data-analyst .
docker run -p 8000:8000 --env-file .env ai-data-analyst
```

### 📡 API Usage

**Endpoint:** `POST /api/`

**Request:** Upload files via multipart/form-data
- 📝 Questions file (`.txt`) - your data questions
- 📊 Data sources: CSV, JSON, Excel, PDF, HTML, images, archives
- 🔢 Multiple files supported simultaneously

**Example with cURL:**
```bash
curl -X POST http://localhost:8000/api/ \
  -F "questions=@questions.txt" \
  -F "data=@data.csv" \
  -F "image=@chart.png"
```

**Response:** JSON with analysis results, generated visualizations, and insights 📈✅

## 🏗️ Solution Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Client Request                          │
│            (Files: TXT, CSV, PDF, Images, etc.)             │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                  FastAPI Application Layer                   │
│                  (app.py - Main Router)                      │
└─────────────────────┬───────────────────────────────────────┘
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
┌──────────────────┐    ┌──────────────────┐
│  File Processing │    │   Data Scraping  │
│   & Extraction   │    │  (data_scrape.py)│
│                  │    │                  │
│ • Archive extract│    │ • Web scraping   │
│ • OCR/Image      │    │ • HTML parsing   │
│ • PDF parsing    │    │ • Table extract  │
│ • Format detect  │    │ • Numeric clean  │
└────────┬─────────┘    └────────┬─────────┘
         │                       │
         └───────────┬───────────┘
                     ▼
         ┌─────────────────────┐
         │   Data Unification  │
         │   (DuckDB Engine)   │
         │                     │
         │ • Multi-table join  │
         │ • SQL generation    │
         │ • Query execution   │
         └──────────┬──────────┘
                    ▼
         ┌─────────────────────┐
         │   AI Analysis Layer │
         │                     │
         │ • Task breakdown    │
         │ • Code generation   │
         │ • LLM orchestration │
         │ • Multi-model retry │
         └──────────┬──────────┘
                    ▼
         ┌─────────────────────┐
         │   Response Builder  │
         │                     │
         │ • Visualization     │
         │ • JSON formatting   │
         │ • File cleanup      │
         └──────────┬──────────┘
                    ▼
         ┌─────────────────────┐
         │   Client Response   │
         │   (JSON + Charts)   │
         └─────────────────────┘
```

**🔑 Key Components:**
- 🌐 **FastAPI Backend**: Handles HTTP requests and orchestrates processing
- 🕷️ **Data Scraper**: Fetches and extracts data from various sources
- 🗄️ **DuckDB Engine**: In-memory database for complex queries
- 🤖 **AI Orchestrator**: Manages multiple LLM providers with fallback
- 🧹 **Cleanup Manager**: Tracks and removes temporary files

## 🛠️ Tech Stack

### 🎯 Core Framework
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=flat-square&logo=python&logoColor=white)

- **FastAPI** - High-performance async web framework 🚀
- **Python 3.11** - Programming language 🐍

### 📊 Data Processing
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

- **Pandas** - Data manipulation and analysis 🐼
- **NumPy** - Numerical computing 🔢
- **DuckDB** - In-memory analytical database 🦆
- **Tabula** - PDF table extraction 📄
- **pdfplumber** - PDF text extraction 📖
- **openpyxl** - Excel file handling 📗

### 🌐 Web Scraping
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=flat-square&logo=selenium&logoColor=white)

- **Playwright** - Browser automation 🎭
- **playwright-stealth** - Anti-detection 🥷
- **BeautifulSoup4** - HTML parsing 🍜
- **httpx** - Async HTTP client ⚡
- **Selenium** - Alternative browser automation 🌐

### 🤖 AI & ML
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![Anthropic](https://img.shields.io/badge/Claude-181818?style=flat-square&logo=anthropic&logoColor=white)
![Google](https://img.shields.io/badge/Gemini-4285F4?style=flat-square&logo=google&logoColor=white)

- **OpenAI GPT** - Language model 🧠
- **Claude (Anthropic)** - Language model 💭
- **Google Gemini** - Language model ✨
- **Grok (xAI)** - Language model 🚀
- **OCR.space API** - Optical character recognition 👁️

### 📈 Visualization
- **Matplotlib** - Chart generation 📊
- **Seaborn** - Statistical visualizations 🎨
- **NetworkX** - Graph/network visualizations 🕸️

### 🔧 Utilities
- **python-dotenv** - Environment management 🔐
- **python-multipart** - File upload handling 📤
- **chardet** - Character encoding detection 🔤

### 🚢 Deployment
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Uvicorn](https://img.shields.io/badge/Uvicorn-499848?style=flat-square&logo=gunicorn&logoColor=white)

- **Docker** - Containerization 🐳
- **Uvicorn** - ASGI server ⚡

---

## 🙏 Thank You!

Thank you for using AI Data Analyst! This project aims to democratize data analysis by making it accessible through natural language. 💡

**👨‍💻 Created by:** [@heyitsgautham](https://github.com/heyitsgautham)

**🤝 Contributions Welcome!** Feel free to open issues or submit pull requests.

**📜 License:** See [LICENSE](LICENSE) file

---

<div align="center">

### ⭐ Star this repo if you find it helpful!

[![GitHub stars](https://img.shields.io/github/stars/heyitsgautham/data-analyst?style=social)](https://github.com/heyitsgautham/data-analyst/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/heyitsgautham/data-analyst?style=social)](https://github.com/heyitsgautham/data-analyst/network/members)
[![GitHub watchers](https://img.shields.io/github/watchers/heyitsgautham/data-analyst?style=social)](https://github.com/heyitsgautham/data-analyst/watchers)

*Made with ❤️ and AI*

</div>
