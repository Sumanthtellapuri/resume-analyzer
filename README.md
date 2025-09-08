# Resume Analyzer

Production-ready starter for a full-stack Resume Analyzer using React (Vite + Tailwind) and Node.js (Express) with PostgreSQL. PDF parsing via pdf-parse and optional Gemini integration.

## Prerequisites

- Node.js 18+
- PostgreSQL 13+

## Backend Setup

```
cd backend
npm install
```

Create `.env` locally with:

```
PORT=5000
CORS_ORIGIN=http://localhost:5173
DATABASE_URL=postgres://postgres:postgres@localhost:5432/resume_analyzer
PGSSL=false
# GEMINI_API_KEY=your_api_key_here
```

Start server:

```
npm run dev
```

### API Endpoints

- POST `/api/resumes/upload` (multipart field `file`) → analyze & save
- GET `/api/resumes` → list basic info
- GET `/api/resumes/:id` → full record with analysis JSON

## Database

Table `resumes` is created automatically on server start. Uses `JSONB` for nested analysis data.

## Frontend Setup

```
cd frontend
npm install
npm run dev
```

Optional `.env` for frontend:

```
VITE_API_BASE=http://localhost:5000/api
```

## Gemini Integration

Replace the placeholder in `backend/services/analysisService.js` by instantiating `GoogleGenerativeAI` with `GEMINI_API_KEY` and parsing the strict JSON response. Prompt enforces minified JSON, no markdown.

## Notes

- Robust error handling for bad files, corrupted PDFs, DB errors, and API failures.
- Tailwind for modern UI; two tabs: Live Analysis and Historical Viewer.
