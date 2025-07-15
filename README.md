# Todo App with Next.js and PostgreSQL

A simple todo application built with Next.js, TypeScript, Tailwind CSS, and PostgreSQL using Prisma ORM.

## Features

- Add new todos
- Mark todos as completed/uncompleted
- Delete todos
- Persistent storage with PostgreSQL
- Responsive design with Tailwind CSS

## Prerequisites

- Node.js (v18 or higher)
- Docker (for PostgreSQL)
- npm or yarn

## Setup Instructions

1. **Clone or navigate to the project directory:**
   ```bash
   cd todo-app
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start PostgreSQL database:**
   ```bash
   docker run --name todo-postgres -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres
   ```

4. **Set up environment variables:**
   The `.env` file is already configured with:
   ```
   DATABASE_URL="postgresql://postgres:password@localhost:5432/todoapp"
   ```

5. **Run database migrations:**
   ```bash
   npx prisma migrate dev --name init
   ```

6. **Start the development server:**
   ```bash
   npm run dev
   ```

7. **Open your browser:**
   Navigate to [http://localhost:3000](http://localhost:3000)

## Project Structure

```
todo-app/
├── app/
│   ├── api/
│   │   └── todos/
│   │       ├── route.ts          # GET, POST /api/todos
│   │       └── [id]/
│   │           └── route.ts      # PUT, DELETE /api/todos/[id]
│   ├── generated/
│   │   └── prisma/              # Generated Prisma client
│   └── page.tsx                 # Main application page
├── prisma/
│   ├── schema.prisma            # Database schema
│   └── migrations/              # Database migrations
├── .env                         # Environment variables
└── README.md
```

## API Endpoints

- `GET /api/todos` - Fetch all todos
- `POST /api/todos` - Create a new todo
- `PUT /api/todos/[id]` - Update a todo (title or completed status)
- `DELETE /api/todos/[id]` - Delete a todo

## Database Schema

The Todo model includes:
- `id` (String, UUID, Primary Key)
- `title` (String)
- `completed` (Boolean, default: false)
- `createdAt` (DateTime)
- `updatedAt` (DateTime)

## Technologies Used

- **Next.js 15** - React framework with App Router
- **TypeScript** - Type safety
- **Tailwind CSS** - Styling
- **Prisma** - Database ORM
- **PostgreSQL** - Database
- **Docker** - Database containerization

## Troubleshooting

1. **Database connection issues:**
   - Ensure PostgreSQL container is running: `docker ps`
   - Check if port 5432 is available
   - Verify environment variables in `.env`

2. **Prisma client issues:**
   - Regenerate client: `npx prisma generate`
   - Reset database: `npx prisma migrate reset`

3. **Development server issues:**
   - Clear Next.js cache: `rm -rf .next`
   - Reinstall dependencies: `rm -rf node_modules && npm install`

