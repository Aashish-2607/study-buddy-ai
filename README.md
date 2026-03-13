# Workspace

## Overview

StudyPilot - AI-powered study assistant web application built as a hackathon demo.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **AI**: OpenAI via Replit AI Integrations (gpt-5.2)
- **Frontend**: React + Vite, Tailwind CSS, Framer Motion, Recharts, canvas-confetti

## Features

- **Dashboard**: Animated stats (XP, streaks, level), weekly XP chart (recharts), achievements
- **Question Generator**: AI-powered quiz generation by topic with MCQ/short answer/conceptual types. Answer selection with correct/wrong feedback, explanations, scoring
- **AI Mentor**: Streaming chat with StudyPilot AI persona using OpenAI GPT
- **Study Schedule**: Focus timer with Pomodoro sessions
- **Achievements**: XP, levels, streaks, badges

## Structure

```text
artifacts-monorepo/
├── artifacts/
│   ├── api-server/         # Express API server
│   └── study-pilot/        # React + Vite frontend (preview path: /)
├── lib/
│   ├── api-spec/           # OpenAPI spec + Orval codegen config
│   ├── api-client-react/   # Generated React Query hooks
│   ├── api-zod/            # Generated Zod schemas from OpenAPI
│   ├── db/                 # Drizzle ORM schema + DB connection
│   ├── integrations-openai-ai-server/  # OpenAI server client
│   └── integrations-openai-ai-react/   # OpenAI React hooks
```

## DB Tables

- `study_sessions` - Focus timer sessions with XP earned
- `quiz_results` - Quiz completion history with scores
- `conversations` - AI mentor chat conversations
- `messages` - Chat messages per conversation

## Key API Routes

- `POST /api/study/generate-questions` - AI question generation
- `GET/POST /api/study/sessions` - Focus sessions
- `GET /api/study/stats` - Student stats (XP, streak, level, achievements)
- `POST /api/study/quiz-results` - Save quiz result
- `GET/POST /api/openai/conversations` - Mentor conversations
- `POST /api/openai/conversations/:id/messages` - Streaming AI chat
