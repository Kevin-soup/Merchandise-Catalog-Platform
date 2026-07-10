# Merchandise Catalog Platform

A full-stack merchandise catalog application built using a microservice architecture.

The platform follows RESTful design principles. Services communicate over HTTP using JSON and expose independent CRUD endpoints for their respective domains.


## System Components

### Main Program 
- **Merchandise Catalog Website (UI)**
- A user facing website to browse products, search by name, filter by category, and view item details with images.
- Responsibilities: browse products, search by keyword, filter by category, display product images, and admin CRUD operations.

### Microservice A 
- **Announcement Banner**
- A lightweight API for posting and retrieving short announcements used by the site.
- Responsibilities: saving and retrieving a single announcement payload with optional expiration.

### Microservice B 
- **Admin Authorization**
- Centralized admin identity and access control.
- Responsibilities: authenticating admins, issuing/verifying tokens, and enforcing role-based permissions on protected actions.

### Microservice C 
- **Image Service**
- Stores product images and serves originals + metadata.
- Responsibilities: uploading images (admin-protected), streaming images to the UI, and exposing metadata.

### Microservice D
- **Product Catalog Service**
- Manages the product/item dataset.
- Responsibilities: creating, listing, updating, and deleting products.


## Architecture
```
                          Browser UI
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ▼                   ▼                   ▼
  Product Catalog      Image Service      Auth Service
   (CRUD Products)    (Upload & Serve)   (Admin Verification)
          │
          │
          ▼
 Announcement Service
   (Site Announcements)

Protected Operations
────────────────────────────────────────────
Admin → Auth Service → Catalog/Image Services
Header: x-admin-token
```


## Running Locally

See each subfolder’s README for environment variable templates.

Install dependencies and run each service
```bash
npm install
check package.json for start scripts
```
