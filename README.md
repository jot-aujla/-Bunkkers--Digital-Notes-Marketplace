
# BUNKKERS — Local-first marketplace

## Requirements
- Node.js 20.9+ (Node 22 LTS recommended)
- Windows 10/11

## Setup
1. Extract this folder.
2. Open PowerShell in the extracted `bunkkers` folder.
3. Run `npm install`.
4. Copy `.env.example` to `.env.local`.
5. Change `ADMIN_PASSWORD` to a long private password. Keep `.env.local private.
6. Run `npm run dev` and open http://localhost:3000.

## Admin
Create an account using the email in `ADMIN_EMAIL` and the exact password in `ADMIN_PASSWORD`. That account receives admin role at registration. If the account was created before setting the environment values, remove `data/bunkkers.json` only if you are happy to erase all local users and data, then restart and register again.

## Local storage
- `data/bunkkers.json`: users, sessions, notes metadata, purchases, payment submissions, withdrawals and reviews.
- `storage/notes`: uploaded note files.
- `storage/payments`: payment screenshots.

Back up both `data` and `storage` regularly. Do not upload `.env.local`, `data`, or `storage` to public repositories.

## Current workflow
- Students register/login. Passwords are stored as salted scrypt hashes.
- Sellers upload supported documents (maximum 30 MB). Listings require admin approval.
- Buyers submit UPI transaction reference and screenshot. Admin manually checks the payment and approves/rejects. Approval unlocks note download and credits the seller's 80% share; platform share is 20%.
- Withdrawal requests require at least ₹500 and are marked paid/rejected by admin.

## Important limitations
This is a local single-computer prototype, not a public multi-user production service. The JSON file database is appropriate for local testing only; it does not provide robust concurrent transactions, cloud backup, email verification, password reset, Google OAuth, automated UPI verification, or secure multi-device access. Never use it for real financial transactions without a production-grade database, hardened authorization, backups, and independent security review. Only upload files you have rights to distribute.
