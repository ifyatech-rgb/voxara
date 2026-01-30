# API Integration Quick Reference

## 🎯 Where Each API is Used

### 1. OpenAI API (Script Generation)
**File**: `app/api/scripts/generate/route.ts` (Line 7-9)
```typescript
const openai = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,  // ← Add to .env
});
```

### 2. Google OAuth (Authentication)
**File**: `lib/auth.ts` (Line 10-13)
```typescript
GoogleProvider({
  clientId: process.env.GOOGLE_CLIENT_ID,      // ← Add to .env
  clientSecret: process.env.GOOGLE_CLIENT_SECRET, // ← Add to .env
}),
```

### 3. HeyGen API (Video Generation - Phase 2)
**File**: `app/api/scripts/[id]/generate-video/route.ts` (Line 79)
- Currently placeholder
- Needs implementation (see comments in file)

### 4. Email Provider (Optional Auth)
**File**: `lib/auth.ts` (Line 14-24)
```typescript
EmailProvider({
  server: {
    host: process.env.EMAIL_SERVER_HOST,     // ← Add to .env
    port: process.env.EMAIL_SERVER_PORT,     // ← Add to .env
    // ... more email config
  },
}),
```

---

## 📁 File Structure

```
your-project/
├── .env                    ← ADD ALL API KEYS HERE
├── lib/
│   └── auth.ts            ← Google OAuth & Email config
├── app/
│   └── api/
│       └── scripts/
│           ├── generate/
│           │   └── route.ts    ← OpenAI API (already integrated)
│           └── [id]/
│               └── generate-video/
│                   └── route.ts  ← HeyGen API (needs implementation)
```

---

## ⚡ Quick Setup (3 Steps)

### Step 1: Create `.env` file
```bash
cp .env.example .env
```

### Step 2: Add API Keys to `.env`
```env
# Required
OPENAI_API_KEY=sk-your-key-here
NEXTAUTH_SECRET=generate-with-openssl-rand-base64-32

# Optional
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret
HEYGEN_API_KEY=your-heygen-key
```

### Step 3: Restart Server
```bash
npm run dev
```

---

## 🔗 Get API Keys

| API | Where to Get | Link |
|-----|-------------|------|
| **OpenAI** | OpenAI Platform | https://platform.openai.com/api-keys |
| **Google OAuth** | Google Cloud Console | https://console.cloud.google.com/ |
| **HeyGen** | HeyGen Dashboard | https://www.heygen.com |

---

## ✅ Integration Status

- ✅ **OpenAI** - Fully integrated, just add API key
- ✅ **Google OAuth** - Fully integrated, just add credentials  
- ⏳ **HeyGen** - Needs implementation (see `generate-video/route.ts`)
- ✅ **Email** - Fully integrated, just add SMTP config

---

**For detailed instructions, see `API_INTEGRATION_GUIDE.md`**
