# Asset Hub

Modern full-stack asset management platform with Next.js 15, Supabase, dashboard analytics, Gemini AI support, and social integration.

## Features

- **Dashboard Analytics**: Real-time portfolio tracking with charts and KPI cards
- **Asset Management**: Track stocks, crypto, and other investments
- **Trading Strategies**: View and manage trading strategies with performance metrics
- **AI Assistant**: Built-in Gemini AI chat for portfolio insights
- **Social Integration**: Link your social media and display content
- **Authentication**: Secure login with Supabase (email/password + OAuth)
- **Responsive Design**: Dark-themed UI with Tailwind CSS

## Tech Stack

- **Frontend**: Next.js 15 (App Router), React 18, TypeScript
- **Styling**: Tailwind CSS
- **Database & Auth**: Supabase (PostgreSQL + Row Level Security)
- **AI**: Google Gemini API
- **Charts**: Recharts
- **Deployment**: Vercel (recommended)

## Getting Started

### Prerequisites

- Node.js 18+ and npm/yarn
- Supabase account (free tier works)
- Google Gemini API key

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/vinay031098/asset-hub.git
cd asset-hub
```

2. **Install dependencies**

```bash
npm install
```

3. **Set up Supabase**

- Go to [supabase.com](https://supabase.com) and create a new project
- Copy your project URL and anon key
- Run the SQL from `supabase/schema.sql` in the Supabase SQL editor

4. **Configure environment variables**

Create `.env.local` in the root directory:

```env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Gemini AI
GEMINI_API_KEY=AIzaSyBjsCshi-zvr0qnt9njArEThc28LHTgh2Q
```

5. **Run the development server**

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
asset-hub/
├── src/
│   ├── app/
│   │   ├── (public)/          # Public routes (landing, login)
│   │   ├── (dashboard)/        # Protected dashboard routes
│   │   ├── api/
│   │   │   └── ai/chat/        # AI chat endpoint
│   │   └── styles/
│   ├── components/
│   │   ├── layout/             # Navbar, Footer, Sidebar
│   │   ├── dashboard/          # StatCard, AssetTable, Charts
│   │   └── ai/                 # ChatWidget
│   ├── lib/
│   │   ├── supabaseClient.ts   # Client-side Supabase
│   │   ├── supabaseServer.ts   # Server-side Supabase
│   │   └── aiClient.ts         # Gemini AI wrapper
│   └── types/
├── supabase/
│   └── schema.sql              # Database schema
├── public/
├── package.json
├── tsconfig.json
├── tailwind.config.mjs
└── next.config.mjs
```

## Database Schema

The Supabase schema includes:

- `profiles` - User profiles linked to auth
- `portfolios` - User portfolios
- `assets` - Individual assets (stocks, crypto, etc.)
- `strategies` - Trading strategies
- `strategy_performance` - Daily strategy performance data
- `social_links` - Social media links
- `activity_log` - User activity tracking

See `supabase/schema.sql` for the complete schema with RLS policies.

## Development

### Adding New Pages

- **Public pages**: Add to `src/app/(public)/`
- **Dashboard pages**: Add to `src/app/(dashboard)/`

### Creating Components

All components go in `src/components/` organized by feature.

### API Routes

API routes are in `src/app/api/`. The AI chat endpoint is at `/api/ai/chat`.

## Deployment

### Deploy to Vercel

1. Push your code to GitHub
2. Import the project in [Vercel](https://vercel.com)
3. Add environment variables in Vercel dashboard
4. Deploy

### Environment Variables for Production

Make sure to set these in your Vercel project settings:

- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- `GEMINI_API_KEY`

## Key Files to Create Next

After setting up, you'll need to create these core files:

1. `postcss.config.mjs` - PostCSS configuration for Tailwind
2. `tailwind.config.mjs` - Tailwind theme configuration  
3. `src/styles/globals.css` - Global styles with Tailwind directives
4. `src/lib/supabaseClient.ts` - Supabase client helper
5. `src/lib/supabaseServer.ts` - Supabase server helper
6. `src/lib/aiClient.ts` - Gemini AI client
7. `src/app/(public)/layout.tsx` - Public layout
8. `src/app/(public)/page.tsx` - Landing page
9. `src/app/(dashboard)/layout.tsx` - Dashboard layout
10. `src/app/(dashboard)/dashboard/page.tsx` - Main dashboard
11. `src/app/api/ai/chat/route.ts` - AI chat API
12. `src/components/ai/ChatWidget.tsx` - AI chat UI
13. `supabase/schema.sql` - Database schema

## License

MIT

## Contributing

Pull requests are welcome! Please open an issue first to discuss major changes.
