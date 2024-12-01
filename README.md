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

4. Update the variables in your `.env`:

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

We welcome contributions to improve this T3 blueprint project! Here's how you can help:

### How to Contribute

1. **Fork the Repository**

   - Fork the repo to your GitHub account
   - Clone your fork locally

2. **Create a Branch**

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Your Changes**

   - Write clear, concise commit messages
   - Keep changes focused and atomic
   - Add tests if applicable
   - Update documentation as needed

4. **Code Style**

   - Follow the existing code style
   - Use TypeScript strict mode
   - Run `npm run lint` before committing
   - Ensure all tests pass with `npm run test`

5. **Submit a Pull Request**
   - Push your changes to your fork
   - Submit a PR with a clear title and description
   - Reference any relevant issues
   - Wait for review and address any feedback

### Development Guidelines

- Keep the blueprint simple and maintainable
- Avoid adding opinionated features
- Document any new features or changes
- Ensure backwards compatibility
- Test your changes thoroughly

### Bug Reports

- Use the GitHub Issues tab
- Include steps to reproduce
- Specify your environment details
- Provide error messages if any

## License

MIT License

Copyright (c) 2024 Eddie Zeng

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
