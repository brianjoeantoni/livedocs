# LiveDocs

LiveDocs is a collaborative rich-text document editor built with Next.js. It lets authenticated users create documents, invite collaborators with viewer or editor access, edit together in real time, and discuss content through anchored comments and mentions.

## Features

- Clerk-powered sign-up, sign-in, and user profiles
- Create, rename, list, and delete documents
- Real-time co-editing with active collaborator presence
- Role-based sharing: viewers can read; editors can update content and manage sharing
- Rich-text editing with headings, inline formatting, alignment, undo, and redo
- Threaded comments, mentions, and resolved comment states
- In-app notifications for document access and collaboration activity

## Tech stack

- [Next.js 14](https://nextjs.org/) with TypeScript and the App Router
- [React](https://react.dev/) and [Tailwind CSS](https://tailwindcss.com/)
- [Clerk](https://clerk.com/) for authentication and user management
- [Liveblocks](https://liveblocks.io/) for collaborative rooms, presence, comments, and inbox notifications
- [Lexical](https://lexical.dev/) for the rich-text editor
- [Sentry](https://sentry.io/) for error monitoring

## Getting started

### Prerequisites

- Node.js 18.17 or later
- A Clerk application
- A Liveblocks project

### Installation

1. Clone the repository and install dependencies:

   ```bash
   git clone <your-repository-url>
   cd livedocs
   npm install
   ```

2. Create `.env.local` and configure the required credentials:

   ```env
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   CLERK_SECRET_KEY=your_clerk_secret_key
   LIVEBLOCKS_SECRET_KEY=your_liveblocks_secret_key
   ```

   Add the usual Clerk redirect URLs if they are not already configured in your Clerk dashboard. Sentry configuration is optional for local development.

3. Start the development server:

   ```bash
   npm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000).

## Available scripts

```bash
npm run dev    # Start the development server
npm run build  # Create a production build
npm run start  # Run the production server
npm run lint   # Run ESLint
```

## How collaboration works

Each document is represented by a Liveblocks room. The room stores its title, owner, and per-user access permissions. Liveblocks synchronizes editor state, collaborator presence, comments, and inbox events in real time; Clerk provides the authenticated user identity used to authorize access.

## Project structure

```text
app/                    Routes, API endpoints, layout, and providers
components/             Document, sharing, commenting, and editor UI
components/editor/      Lexical editor and toolbar plugins
lib/actions/            Server actions for rooms, access, and users
lib/                    Liveblocks client and shared utilities
styles/                 Editor and theme styles
```

## Deployment

Deploy the app to a Node.js-compatible host such as Vercel. Configure the same Clerk and Liveblocks environment variables in the deployment environment, and ensure the Clerk application permits the production domain.

## License

No license has been specified for this repository.
