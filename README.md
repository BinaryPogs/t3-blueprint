# T3 App Blueprint

This is a [T3 Stack](https://create.t3.gg/) project bootstrapped with `create-t3-app` and enhanced with Prisma, Clerk authentication, and shadcn/ui components.

## Features

- ✨ T3 Stack (Next.js, TypeScript, Tailwind CSS)
- 🔐 Clerk Authentication
- 🗃️ Prisma ORM with PostgreSQL
- 🎨 shadcn/ui Components
- 🪝 Clerk Webhook Integration for User Sync

## Prerequisites

- Node.js (v16 or higher)
- npm
- PostgreSQL database
- [Clerk](https://clerk.com/) account

## Getting Started

1. Clone this repository

```bash
git clone git@github.com:BinaryPogs/t3-blueprint.git
cd t3-blueprint
```

2. Install dependencies

```bash
npm install
```

3. Set up your environment variables by copying the example file:

```bash
cp .env.example .env
```

4. Update the following variables in your `.env`:

```
# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_publishable_key
CLERK_SECRET_KEY=your_secret_key
CLERK_WEBHOOK_SECRET=your_webhook_secret

# Database
DATABASE_URL="postgresql://user:password@localhost:5432/your_database"
```

5. Initialize Prisma and run migrations:

```bash
npx prisma generate
npx prisma db push
```

## Setting up Clerk Webhook

1. Go to [Clerk Dashboard](https://dashboard.clerk.com/)
2. Navigate to your application's webhooks section
3. Create a new webhook endpoint
4. Set the endpoint URL to: `<your-domain>/api/webhook/clerk`
5. Select the following events:
   - user.created
   - user.updated
   - user.deleted

### Local Development with Webhook

To test webhooks locally:

1. Install and run unTun:

```bash
npx untun@latest tunnel http://localhost:3000
```

2. Copy the generated URL and add `/api/webhook/clerk` to it
3. Update your webhook URL in Clerk dashboard with this full URL

## Installing shadcn/ui Components

This project comes with shadcn/ui preconfigured. To add new components:

```bash
npx shadcn-ui@latest add [component-name]
```

Example to add the button component:

```bash
npx shadcn-ui@latest add button
```

Common components you might want to add:

- button
- card
- input
- form
- toast

## Development

Run the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
├── src/
│   ├── pages/
│   │   ├── api/
│   │   │   └── webhook/
│   │   │       └── clerk.ts    # Clerk webhook handler
│   ├── server/
│   │   └── db.ts              # Prisma client configuration
│   └── styles/
│       └── globals.css        # Global styles
├── prisma/
│   └── schema.prisma         # Database schema
└── components/
    └── ui/                   # shadcn/ui components
```

## Additional Notes

- The webhook integration automatically syncs user data between Clerk and your PostgreSQL database
- Make sure your PostgreSQL database is running before starting the application
- Keep your environment variables secure and never commit them to version control

## Common Issues

1. **Webhook not working locally**: Make sure unTun is running and your webhook URL is correctly set in Clerk dashboard
2. **Database connection issues**: Verify your DATABASE_URL is correct and PostgreSQL is running
3. **Missing environment variables**: Ensure all required variables are set in your .env file

## Contributing

[Add your contribution guidelines here]

## License

[Add your license information here]
