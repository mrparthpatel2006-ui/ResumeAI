# 🎯 AI Resume Analyzer & ATS Auditor (Summer Project)

A full-stack, AI-powered Resume Analyzer and ATS Optimization platform built with **Next.js 16 (App Router)**, **TypeScript**, **Tailwind CSS**, **SQLite (Prisma ORM)**, and **Google Gemini AI**.

---

## 🌟 Key Features

1. **🔐 Authentication & User Accounts**:
   - Secure Sign Up / Login with hashed passwords (`bcryptjs`) & JWT session cookies.
   - **1-Click Instant Demo Login** for quick evaluations & live presentations.
   - Persistent User History in local SQLite database.

2. **📄 Multi-Format Resume Ingestion**:
   - Drag-and-drop file uploader supporting **PDF**, **DOCX**, and **TXT** files.
   - Live character counter & pre-loaded **Sample Tech Resume** button for testing.

3. **🤖 Intelligent AI & ATS Scoring Engine**:
   - **Overall ATS Compatibility Score (0 - 100)** with animated circular gauge & score grading.
   - **Category Score Breakdown**:
     - *ATS Keyword Density & Semantic Match*
     - *STAR Method Impact & Quantification (Metrics)*
     - *Skills Relevance*
     - *Formatting & Parsing Structure*
   - **Matched vs. Missing Skills Gap Matrix**: Detects missing industry keywords required for the target job.
   - **STAR Bullet Point Rewriter**: Side-by-side Before (weak) vs. After (quantified STAR) bullet point transformations with **1-click copy** and recruiter reasoning.
   - **Critical Red Flags & Strengths** detection.

4. **💼 Career Accelerator Suite**:
   - **AI Interview Coach**: Generates targeted Technical, Behavioral, and Situational questions with suggested answering strategies based on actual resume experiences.
   - **Tailored Cover Letter Generator**: Creates custom, high-converting 3-paragraph cover letters matching candidate experience to target roles.

5. **📊 Dashboard & History**:
   - Audit history tracking with dates, scores, and job titles.
   - Print-ready and **Markdown (.md) Export** feature.
   - Custom Gemini API Key settings management UI.

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Node.js** v18+ (Node v24 recommended)
- **npm** or **pnpm** / **yarn**

### 2. Running Locally

```bash
# Navigate to project directory
cd C:\Users\parth\.gemini\antigravity\scratch\ai-resume-analyzer

# Database is already configured with SQLite dev.db
# Run the development server
npm run dev

# Or run the optimized production build
npm run build
npm start
```

Visit **`http://localhost:3000`** in your browser.

---

## 🔑 Google Gemini AI Configuration

The application includes an **intelligent offline heuristic analyzer**, allowing complete functionality and instant demo testing out-of-the-box even without an API key.

To enable direct inference with **Gemini 2.0 Flash**:
1. Get a free API key at [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Either add it to `.env`:
   ```env
   GEMINI_API_KEY="your-gemini-api-key"
   ```
3. Or enter it directly in the app at **Dashboard -> Settings -> Google Gemini API Key**.

---

## 📁 Project Structure

```
ai-resume-analyzer/
├── prisma/
│   ├── schema.prisma             # SQLite schema (User, Resume, Analysis, SavedTools)
│   └── dev.db                    # Local SQLite database file
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── auth/             # Login, register, demo, me, logout endpoints
│   │   │   ├── analyze/          # PDF/DOCX parsing & AI audit endpoint
│   │   │   ├── history/          # Saved analyses CRUD
│   │   │   ├── generate/         # Cover letter & interview question generation
│   │   │   └── user/settings/    # API key & preferences
│   │   ├── auth/
│   │   │   ├── login/page.tsx    # Login UI
│   │   │   └── register/page.tsx # Register UI
│   │   ├── dashboard/
│   │   │   ├── page.tsx          # Main user dashboard & stats
│   │   │   ├── analyze/page.tsx  # Upload & audit setup
│   │   │   ├── results/[id]/page.tsx # Comprehensive report page
│   │   │   ├── tools/page.tsx    # Cover letter & interview coach hub
│   │   │   └── settings/page.tsx # Gemini API key & profile settings
│   │   ├── layout.tsx            # Root dark-mode layout
│   │   ├── page.tsx              # Modern landing page
│   │   └── globals.css           # Tailwind CSS
│   ├── components/
│   │   ├── Navbar.tsx            # Navigation header with session menu
│   │   ├── FileUpload.tsx        # Drag & drop uploader with sample loader
│   │   ├── ScoreGauge.tsx        # Animated circular score gauge
│   │   ├── CategoryScoreBar.tsx  # Breakdown metric bars
│   │   ├── BulletComparison.tsx  # Side-by-side STAR rewrites with copy
│   │   ├── SkillsBadgeList.tsx   # Matched & missing skills matrix
│   │   ├── InterviewQuestionCard.tsx # Expandable interview prep cards
│   │   └── ExportReportModal.tsx # PDF Print & Markdown exporter
│   ├── lib/
│   │   ├── auth.ts               # JWT signing/verification & bcrypt hashing
│   │   ├── db.ts                 # Prisma SQLite singleton
│   │   ├── parser.ts             # PDF & DOCX text extraction
│   │   ├── ai.ts                 # Gemini API integration
│   │   └── fallbackAnalyzer.ts   # Intelligent offline ATS & STAR engine
│   └── types/
│       └── index.ts              # TypeScript interfaces
├── .env
├── package.json
└── tsconfig.json
```
