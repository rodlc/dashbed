# Dashbed

> Last minute rooms at a last price!

Dashbed est une plateforme de réservation d'hôtels à prix réduit, spécialisée dans les offres de dernière minute.

## Quick Links

| Resource | Link |
|----------|------|
| GitHub Project | [Roadmap & Kanban](https://github.com/users/rodlc/projects/2) |
| Wireframes | [Figma](https://www.figma.com/VOTRE_LIEN_ICI) |
| DB Schema | [Voir ci-dessous](#database-schema) |

## Team

| Name | Role | Squad |
|------|------|-------|
| Alice | Frontend Developer | Deals UI |
| Bob | Backend Developer | Auth |
| Clara | Full-stack Developer | Booking |

## Tech Stack

- **Framework:** Ruby on Rails 7
- **Database:** PostgreSQL
- **Auth:** Devise
- **Frontend:** Hotwire (Turbo + Stimulus)
- **CSS:** Bootstrap 5
- **Mailer:** Action Mailer

## Getting Started

### Prerequisites

- Ruby 3.2+
- Rails 7+
- PostgreSQL 14+
- Node.js 18+

### Installation

```bash
# Clone the repo
git clone git@github.com:rodlc/dashbed.git
cd dashbed

# Install dependencies
bundle install
yarn install

# Setup database
rails db:create db:migrate db:seed

# Start server
rails server
```

### Environment Variables

Create a `.env` file at root (never commit this file):

```env
DATABASE_URL=postgres://localhost/dashbed_development
RAILS_MASTER_KEY=your_master_key
```

## Database Schema

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   users     │     │   deals     │     │  bookings   │
├─────────────┤     ├─────────────┤     ├─────────────┤
│ id          │     │ id          │     │ id          │
│ email       │     │ hotel_name  │     │ user_id     │──┐
│ full_name   │     │ hotel_city  │     │ deal_id     │──┼─┐
│ phone       │     │ hotel_desc  │     │ check_in    │  │ │
│ encrypted_  │     │ hotel_amen  │     │ check_out   │  │ │
│  password   │     │ hotel_rating│     │ status      │  │ │
└─────────────┘     │ room_name   │     │ total_price │  │ │
       ▲            │ room_desc   │     └─────────────┘  │ │
       │            │ price       │            │         │ │
       │            │ discount_   │            │         │ │
       │            │  price      │            │         │ │
       │            └─────────────┘            │         │ │
       │                   ▲                   │         │ │
       └───────────────────┼───────────────────┘         │ │
                           └─────────────────────────────┘ │
                                                           │
```

**Relations:**
- `bookings.user_id` → `users.id`
- `bookings.deal_id` → `deals.id`

## Git Workflow

### Branches

```
main                 # Production-ready code
├── feature/auth     # Authentication features
├── feature/deals    # Deals management
└── feature/booking  # Booking flow
```

### Commit Convention

```
[Squad] Brief description

# Examples:
[Auth] Add Devise configuration
[Deals] Create Deal model with validations
[Booking] Implement booking form
```

### Pull Request Process

1. Create feature branch from `main`
2. Make changes and commit
3. Push and open PR
4. Request review from teammate
5. Address feedback
6. Squash and merge

## Sprint Planning

**Sprint 1** (Dec 18-30)

| Phase | Dates | Stories |
|-------|-------|---------|
| Foundation | Dec 18-19 | Auth setup, Deal model |
| Core UI | Dec 20-24 | Homepage, Deal detail |
| Booking | Dec 23-27 | Booking flow, Confirmation |
| Polish | Dec 27-30 | Email notifications |

## Contributing

1. Pick an issue from the [Project Board](https://github.com/users/rodlc/projects/2)
2. Assign yourself
3. Move to "In Progress"
4. Create feature branch
5. Submit PR when ready
6. Move to "In Review"
7. After merge, move to "Done"

## License

Private - Le Wagon Project
