# ITITIU18055_DangDinhKhang
AI-Driven Multimodal E-Commerce PlatformAn advanced, cost-effective full-stack e-commerce solution specializing in Visual Semantic Search and NLP-Driven Conversational Recommendations for electrical and technical products. By shifting from rigid keyword matching to local high-dimensional vector search, this platform bridges the traditional "search gap" inherent in complex hardware procurement.

##🚀 Core Features
1. Multimodal Semantic Search
Local Image Inference: Utilizes a localized CLIP (Contrastive Language-Image Pre-training) model running entirely on the application server via @xenova/transformers. No external API dependencies or recurring per-image cloud costs.
Vision Transformer (ViT) Processing: Deconstructs product images into contextual visual patches, translating them into a unified 512-dimensional semantic vector space.
High-Performance Vector Matching: Leverages PostgreSQL's pgvector extension to execute lightning-fast Cosine Similarity queries, matching uploaded hardware photos to absolute database coordinates in milliseconds.
2. NLP Recommendation Chat & Human Handover
Lightweight Local NLP: Powered by the compromise library to parse user intent directly inside the Node runtime. Normalizes syntax and performs real-time Noun Extraction to dynamically map domains (category, brand, price constraints).
Contextual Product Injections: Pushes interactive, metadata-driven product card payloads right into the chat stream via Prisma bindings.
Real-Time Realism via WebSockets: Driven by NestJS and Socket.io. If the NLP pipeline encounters high ambiguity or requires deep technical expertise, it flags a seamless Human Handover, instantly routing the session to a live admin dashboard.
3. Enterprise Infrastructure & Commerce Foundations
Edge Middleware Security: Evaluates role-based route permissions via stateless JSON Web Tokens (JWT) before reaching backend application stacks.
ZaloPay Gateway Integration: A secure, webhook-backed sandbox implementation processing transactions with verified HMAC-SHA256 signature signatures.
Reactive UI State: Uses Zustand on the Next.js App Router frontend to eliminate unneeded component re-renders while unifying the global search space, chat modules, and persistent shopping cart states.

##🛠️ Tech Stack
LayerTechnologies
FrontendNext.js 15+ (App Router), Zustand, TailwindCSS
BackendNestJS, Socket.io (WebSockets), Prisma ORM
Database & AIPostgreSQL + pgvector, @xenova/transformers (CLIP Model)
Librariescompromise (NLP), jose (JWT at Edge)
Payment GatewayZaloPay SDK (Sandbox)

##🔧 Installation & Quick StartEnsure you have Node.js (v18+) and PostgreSQL installed locally.
1. Clone & Navigate
Bash
git clone https://github.com/khakzy12/ITITIU18055_DangDinhKhang.git
cd ITITIU18055_DangDinhKhang
2. Environment Configuration
Create a .env file in the root directory of both your frontend and backend setups (referencing .env.example).
Database Credentials
DATABASE_URL="postgresql://kha:npg_VYKdGCD40Rnz@ep-morning-hill-a1yp0yb5-pooler.ap-southeast-1.aws.neon.tech/tech?sslmode=require&channel_binding=require"

Authentication
JWT_SECRET="bd638d847bdc79d7407b0d0cda4f18bc2374630eb4492b182e0a7ebab5c81ce0"

CORS: Next.js dev server
FRONTEND_ORIGIN=http://localhost:3000

ZaloPay Credentials (Sandbox)
ZALOPAY_APP_ID=2554
ZALOPAY_KEY1=sdngKKJmqEMzvh5QQcdD2A9XBSKUNaYn
ZALOPAY_KEY2=trMrHtvjo6myautxDUiAcYsVtaeQ8nhf
ZALOPAY_CALLBACK_URL=http://localhost:3001/api/payments/zalopay-callback

3. Backend Setup (NestJS)
Bash
cd backend
npm install
npx prisma db push # Pushes schema and sets up vector capacities
npm run start:dev

4. Frontend Setup (Next.js)
Bash
cd ../frontend
npm install
npm run dev
The system will now be active with the frontend running at http://localhost:3000 and the backend listening at http://localhost:8000.
##📊 System Architecture Visualized

## 📊 System Architecture Visualized

```text
[User Browser] 
       │ 
  (Next.js App Router) ─── [Zustand State Engine]
       │
 (Edge Middleware / JWT Verification)
       │
 [NestJS Backend Engine] ◄─── (Socket.io WebSockets) ─── [Admin Handover Terminal]
       ├───► [@xenova/transformers / CLIP ViT Engine]
       │
 [PostgreSQL Database] 
       └───► (pgvector / Cosine Similarity Index)
       
##📝 Project Evaluation & Roadmap
Top-K Accuracy Metrics: Evaluated against traditional classification engines (ResNet50). CLIP's zero-shot visual patch analysis yielded drastically superior accuracy mappings across unlabelled hardware components.
System Resilience: Implemented a definitive fallback mechanism. When natural processing metrics fall below a 78% certainty threshold, Socket.io structures gracefully trigger human escalation protocols.
Next Horizon: Integration of multi-view 3D item embeddings to ensure complete structural clarity of complex hardware models from arbitrary user snapshots.
