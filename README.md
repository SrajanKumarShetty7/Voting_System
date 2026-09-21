<h1 align="right"><strong>Voting_System</strong></h1>

Repository navigation
Code
Issues
Pull requests
Voting_System
/Voting_System-main/
SrajanKumarShetty7
SrajanKumarShetty7
2 months ago
Voting_System
/Voting_System-main/
Name	Last commit date
..
backend
2 months ago
frontend
2 months ago
.gitignore
2 months ago
README.md
2 months ago
package-lock.json
2 months ago
package.json
2 months ago
README.md
Secure National Biometric Voting System (Demo)
A full-stack academic demo of a Secure National Biometric Voting System with:

Mock India-wide voter database (state/constituency)
Webcam face capture overlay (face-api.js in-browser when models are provided)
Simulated fingerprint pattern scan (pattern → hashed template)
Fraud flagging + IP logging on biometric mismatch
Important: This is a demo system.

It does not connect to real Aadhaar or any government systems.
Biometric matching is simulated using hashed templates/descriptors.
Tech stack
Frontend: React + TypeScript (Vite) + Tailwind + Framer Motion + Three.js + Chart.js
Backend: Node.js + Express
Database: MongoDB (Mongoose)
Auth: JWT (voter + admin roles)
Folder structure
frontend/ React app
backend/ Express API
Prerequisites
Node.js 18+ (recommended)
MongoDB running locally (or a MongoDB URI)
Backend setup
cd backend
cp .env.example .env
npm install
npm run seed
npm run dev
Backend runs at http://localhost:5001 by default (see backend/.env.example).

Seed script creates:

Admin: admin / admin123
Voters:
Priya Sharma — 123456789012
Arjun Singh — 234567890123
Meera Nair — 345678901234
Frontend setup
cd frontend
cp .env.example .env
npm install
npm run dev
Frontend runs at http://localhost:5173.

Demo flow
Open the landing page and click Verify & Vote.
Enter one of the seeded voters' Full Name + 12-digit Aadhaar.
Capture face (webcam) and draw a fingerprint pattern.
Click Complete Verification to receive a JWT session.
Vote once on the Voting Dashboard.
Open Admin Dashboard and login to see vote stats + charts.
Face models (optional)
For real face-api.js detection + descriptors, place the face-api.js model files under:

frontend/public/models/

If models are missing, the UI falls back to a simulated face descriptor so the demo remains runnable.

Generate 10,000 mock voters
cd backend
npm run generate:voters
This inserts 10,000 mock voter records with state/constituency and empty biometric templates (first verification enrolls them).

Security features implemented (demo)
Aadhaar validation (12 digits)
Rate limiting (API)
Password hashing for admin (bcrypt)
JWT auth middleware and role checks
Duplicate vote prevention (atomic hasVoted update + unique Vote record)
Input sanitization (express-mongo-sanitize), basic hardening (helmet, hpp)
Admin features
Real-time-ish stats refresh
Fraud logs (IP + mismatch reason)
State-wise vote breakdown
Search voter by Aadhaar + lock/unlock
Notes
Biometrics are simulated using hashed templates/descriptors for academic demonstration.
For production systems, use certified hardware, audited enrollment, and privacy-preserving storage.
