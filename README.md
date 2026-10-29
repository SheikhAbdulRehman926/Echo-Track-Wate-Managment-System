# ECO Track Waste Management System

ECO Track is a production-ready Next.js App Router platform for municipal waste
management. It combines Supabase (Postgres + PostGIS + Auth + Realtime) with
Mapbox to deliver live vehicle tracking, zone compliance, and SDG 12 guidance.

Aligned with UN SDG 12 (Responsible Consumption and Production), the platform
prioritizes waste reduction, segregation, and efficient collection for real-world
smart-city deployment.

## Key Features

- Live map with vehicle positions, routes, authorized zones, and alerts
- Role-based dashboards for citizens, drivers, and administrators
- SDG 12 household guidance content for safe waste handling
- Supabase-ready schema with PostGIS geometry and RLS notes

## Architecture Overview

- Frontend: Next.js (App Router), Tailwind, Mapbox GL
- Backend: Next.js API Routes for vehicles, zones, notifications
- Database: Postgres + PostGIS (Supabase), with RLS policies
- Realtime: Supabase Realtime or WebSockets for live vehicle positions

## Pages

- `app/(public)/page.tsx` Operations map (primary homepage)
- `app/(public)/sustainability/page.tsx` SDG 12 household guidance
- `app/(dashboards)/citizen/page.tsx` Citizen services dashboard
- `app/(dashboards)/driver/page.tsx` Driver navigation dashboard
- `app/(dashboards)/admin/page.tsx` Admin analytics dashboard

## API Routes

- `GET /api/vehicles` live vehicle telemetry (fallback data included)
- `GET /api/zones` authorized dumping zones and boundaries
- `GET /api/notifications` operational alerts and warnings

## Database Schema

- `vehicles` live vehicle status, mode, capacity, and location
- `vehicle_positions` realtime location history
- `routes` planned collection routes
- `dump_zones` authorized dumping areas
- `illegal_dumps` citizen and sensor-reported illegal sites
- `collection_events` recorded waste volumes and timestamps

See `supabase/schema.sql` for PostGIS-enabled tables and RLS notes.

## Environment Setup

Copy `.env.example` to `.env.local` and provide values:

- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`
- `NEXT_PUBLIC_MAPBOX_TOKEN`

## Development

```bash
npm install
npm run dev
```

Open `http://localhost:3000` to view the live map.

## Deployment

See `docs/deployment-checklist.md` for production checklist and Vercel setup.
