# CONNEXUS
 Backend repository

 Backend Architecture
 The backend supports the dApp functionalities ensuring data consistency, blockchain interaction, and scalability

 Technologies
 Blockchain:
 Smart contracts:
 Server:
 Database:

 Services
 1. Authentication
    Wallet based authentication (no centralised credentials)
 2. Job posting: Payment terms linked to a smart contract
 3. Smart contract management: Escrow functionality for payments. Contracts validation for deliveries
 4. Payment Processing: Cryptocurrency transactions (GHRT and other tokens). Cross border payment integrations
 5. Reputation system: Dynamic score calculation based on performance and staking
 6. Staking: Stake management (GHRT tokens). Bonus calculations
 7. Governance: Token based voting
 8. security: Audited contracts and API endpoints. Data encryption for sensitive metadata

 Pages And API
 1. Home Page
    Front page features
    overview of the platform
    Links to sign up, sig in, and wallet connection
    Key stats (Number of jobs posted, users registered, etc)
    Featured jobs and testimonials

 Backend APIs 
 
1. GET /stats 
 
Fetch key stats (jobs posted, users registered, etc.) 
 
Response: { jobsPosted, usersRegistered, jobsCompleted } 
 
 
 
2. GET /featured-jobs 
 
Fetch a list of featured jobs 
 
Response: { jobs: [{ id, title, employer, description, payment }] } 
 
 
 
 
2. Sign-Up/Sign-In 
 
Frontend Page Features 
 
Wallet-based sign-in (MetaMask or similar) 
 
Option to sign in as employer or job seeker 
 
 
Backend APIs 
 
1. POST /auth/login 
 
Authenticate user via wallet signature 
 
Request: { walletAddress, signature } 
 
Response: { userId, token, role } 
 
 
 
2. POST /auth/register 
 
Register a new user 
 
Request: { walletAddress, role } 
 
Response: { userId, token } 
 
 
 
 
3. Dashboard 
 
Frontend Page Features 
 
Separate dashboards for employers and job seekers 
 
Job status tracking (active, pending, completed) 
 
Staking and reputation display 
 
 
Backend APIs 
 
1. GET /dashboard 
 
Fetch dashboard data (jobs, reputation, staking) 
 
Response: { jobs: [], reputation, staking } 
 
 
 
2. GET /jobs?status=active 
 
Fetch user-specific job list by status 
 
Response: { jobs: [{ id, title, status, deadline }] } 
 
 
 
 
4. Job Listing Page 
 
Frontend Page Features 
 
Job creation form for employers 
 
Filters for job seekers (category, payment, etc.) 
 
Job details view 
 
 
Backend APIs 
 
1. POST /jobs (Employer) 
 
Create a new job posting 
 
Request: { title, description, payment, deadline, skillsRequired } 
 
Response: { jobId } 
 
 
 
2. GET /jobs (Job Seeker) 
 
Fetch available job postings 
 
Query params: ?category=&skills= 
 
Response: { jobs: [{ id, title, description, payment }] } 
 
 
 
3. GET /jobs/:id 
 
Fetch details of a specific job 
 
Response: { id, title, description, employer, payment, deadline } 
 
 
 
 
5. Smart Contract Interaction Page 
 
Frontend Page Features 
 
Smart contract status visualization 
 
Trigger milestones (e.g., job acceptance, completion) 
 
 
Backend APIs 
 
1. POST /contracts 
 
Create a smart contract for a job 
 
Request: { jobId, employer, freelancer, amount } 
 
Response: { contractId, escrowAddress } 
 
 
 
2. POST /contracts/:id/complete 
 
Mark a job as completed 
 
Request: { freelancerProof } 
 
Response: { success: true } 
 
 
 
3. GET /contracts/:id 
 
Fetch smart contract details 
 
Response: { contractId, status, milestones } 
 
 
 
 
6. Profile Page 
 
Frontend Page Features 
 
Display user details (wallet, reputation, jobs completed) 
 
Staking management (stake/unstake tokens) 
 
 
Backend APIs 
 
1. GET /users/:id 
 
Fetch user profile data 
 
Response: { id, wallet, reputation, jobsCompleted, staking } 
 
 
 
2. POST /staking 
 
Stake GHRT tokens 
 
Request: { userId, amount } 
 
Response: { newStakingBalance } 
 
 
 
3. POST /unstaking 
 
Unstake GHRT tokens 
 
Request: { userId, amount } 
 
Response: { newStakingBalance } 
 
 
 
 
7. Governance Page 
 
Frontend Page Features 
 
Propose platform changes 
 
Vote on proposals 
 
 
Backend APIs 
 
1. POST /proposals 
 
Submit a new proposal 
 
Request: { title, description, stakingAmount } 
 
Response: { proposalId } 
 
 
 
2. GET /proposals 
 
Fetch all active proposals 
 
Response: { proposals: [{ id, title, votesFor, votesAgainst }] } 
 
 
 
3. POST /proposals/:id/vote 
 
Vote on a proposal 
 
Request: { vote: "for" | "against" } 
 
Response: { success: true } 
 
 
 
 
8. Notifications 
 
Frontend Page Features 
 
Real-time notifications for job updates, payments, etc. 
 
 
Backend APIs 
 
1. GET /notifications 
 
Fetch user notifications 
 
Response: { notifications: [{ id, message, status }] } 
 
 
 
2. PATCH /notifications/:id 
 
Mark a notification as read 
 
Response: { success: true } 
 
 
 
 
API Summary 
 
Here is a concise API structure for easy backend development: 
 
/auth: Authentication 
 
/jobs: Job management 
 
/contracts: Smart contract operations 
 
/dashboard: User-specific data 
 
/staking: Staking-related actions 
 
/proposals: Governance and voting 
 
/notifications: User notifications 
 
 
 
Note: This roadmap is subject to changes
