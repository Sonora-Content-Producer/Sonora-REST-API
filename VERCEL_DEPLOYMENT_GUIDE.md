# 🚀 Vercel Deployment Guide for Sonora REST API

## Prerequisites

✅ **Vercel CLI installed and logged in**
✅ **Django project configured for production**
✅ **Database accessible from Vercel**
✅ **Environment variables ready**

## 🎯 Quick Deploy

### 1. **Deploy to Vercel**
```bash
# From the Sonora-REST-API directory
vercel --prod
```

### 2. **Set Environment Variables**
```bash
# Set all required environment variables
vercel env add SECRET_KEY
vercel env add DB_NAME
vercel env add DB_USER
vercel env add DB_USER_PASSWORD
vercel env add DB_HOST
vercel env add DB_PORT
vercel env add GOOGLE_OAUTH2_CLIENT_ID
vercel env add GOOGLE_OAUTH2_CLIENT_SECRET
vercel env add GEMINI_API_KEY
vercel env add OPENAI_API_KEY
vercel env add ANTHROPIC_API_KEY
vercel env add FRONTEND_URL
vercel env add BACKEND_BASE_URL
vercel env add STRIPE_PUBLISHABLE_KEY
vercel env add STRIPE_SECRET_KEY
vercel env add STRIPE_WEBHOOK_SECRET
vercel env add ADDITIONAL_CORS_ORIGINS
```

## 🔧 Step-by-Step Deployment

### Step 1: **Prepare Your Project**
```bash
cd Sonora-REST-API

# Make sure all changes are committed
git add .
git commit -m "Prepare for Vercel deployment"
```

### Step 2: **Configure Environment Variables**

#### Option A: Via Vercel Dashboard
1. Go to [vercel.com/dashboard](https://vercel.com/dashboard)
2. Select your `sonora-rest-api` project
3. Go to **Settings** → **Environment Variables**
4. Add each variable from `vercel.env.template`

#### Option B: Via Vercel CLI**
```bash
# Set each environment variable
vercel env add SECRET_KEY production
vercel env add DB_NAME production
vercel env add DB_USER production
vercel env add DB_USER_PASSWORD production
vercel env add DB_HOST production
vercel env add DB_PORT production
vercel env add GOOGLE_OAUTH2_CLIENT_ID production
vercel env add GOOGLE_OAUTH2_CLIENT_SECRET production
vercel env add GEMINI_API_KEY production
vercel env add OPENAI_API_KEY production
vercel env add ANTHROPIC_API_KEY production
vercel env add FRONTEND_URL production
vercel env add BACKEND_BASE_URL production
vercel env add STRIPE_PUBLISHABLE_KEY production
vercel env add STRIPE_SECRET_KEY production
vercel env add STRIPE_WEBHOOK_SECRET production
vercel env add ADDITIONAL_CORS_ORIGINS production
```

### Step 3: **Deploy to Production**
```bash
# Deploy to production
vercel --prod
```

### Step 4: **Verify Deployment**
```bash
# Check deployment status
vercel ls

# View deployment logs
vercel logs
```

## 🌐 Environment Variables Reference

### **Required Variables**
| Variable | Description | Example |
|----------|-------------|---------|
| `SECRET_KEY` | Django secret key | `your-super-secret-key` |
| `DEBUG` | Debug mode | `False` |
| `ALLOWED_HOSTS` | Allowed hosts | `sonora-rest-api.vercel.app` |
| `DB_NAME` | Database name | `sonora_prod` |
| `DB_USER` | Database user | `sonora_user` |
| `DB_USER_PASSWORD` | Database password | `secure_password` |
| `DB_HOST` | Database host | `your-db-host.com` |
| `DB_PORT` | Database port | `3306` |

### **AI Service Variables**
| Variable | Description | Example |
|----------|-------------|---------|
| `GEMINI_API_KEY` | Google Gemini API key | `AIza...` |
| `OPENAI_API_KEY` | OpenAI API key | `sk-...` |
| `ANTHROPIC_API_KEY` | Anthropic API key | `sk-ant-...` |

### **OAuth & Frontend Variables**
| Variable | Description | Example |
|----------|-------------|---------|
| `GOOGLE_OAUTH2_CLIENT_ID` | Google OAuth client ID | `123456789.apps.googleusercontent.com` |
| `GOOGLE_OAUTH2_CLIENT_SECRET` | Google OAuth client secret | `GOCSPX-...` |
| `FRONTEND_URL` | Frontend URL | `https://sonora-ui.vercel.app` |
| `BACKEND_BASE_URL` | Backend URL | `https://sonora-rest-api.vercel.app` |

### **Stripe Variables**
| Variable | Description | Example |
|----------|-------------|---------|
| `STRIPE_PUBLISHABLE_KEY` | Stripe publishable key | `pk_live_...` |
| `STRIPE_SECRET_KEY` | Stripe secret key | `sk_live_...` |
| `STRIPE_WEBHOOK_SECRET` | Stripe webhook secret | `whsec_...` |

## 🗄️ Database Configuration

### **Important Notes**
- **Vercel serverless functions have a 10-second timeout**
- **Database must be accessible from Vercel's IP ranges**
- **Consider using connection pooling for better performance**

### **Recommended Database Options**
1. **PlanetScale** - MySQL-compatible, serverless
2. **Railway** - Easy deployment, good performance
3. **Supabase** - PostgreSQL with real-time features
4. **AWS RDS** - Enterprise-grade, reliable

### **Database Connection String Example**
```bash
# For PlanetScale
DB_HOST=aws.connect.psdb.cloud
DB_NAME=sonora_production
DB_USER=your_username
DB_USER_PASSWORD=your_password
DB_PORT=3306
```

## 🔍 Troubleshooting

### **Common Issues**

#### 1. **Database Connection Timeout**
```bash
# Check if database is accessible
ping your-db-host.com

# Test connection from Vercel
vercel logs
```

#### 2. **Environment Variables Not Loading**
```bash
# Verify environment variables are set
vercel env ls

# Check if they're assigned to production
vercel env ls --scope=production
```

#### 3. **Build Failures**
```bash
# Check build logs
vercel logs

# Test build locally
vercel build
```

#### 4. **CORS Issues**
```bash
# Verify CORS settings in settings.py
# Check ADDITIONAL_CORS_ORIGINS variable
# Ensure frontend URL is included
```

### **Debug Commands**
```bash
# View all deployments
vercel ls

# View specific deployment
vercel inspect [deployment-url]

# View logs
vercel logs [deployment-url]

# Rollback to previous deployment
vercel rollback
```

## 🚀 Post-Deployment

### **1. Test Your API**
```bash
# Test the health endpoint
curl https://sonora-rest-api.vercel.app/api/health/

# Test authentication
curl https://sonora-rest-api.vercel.app/api/v1/auth/login/
```

### **2. Update Frontend**
```bash
# Update your frontend to use the new backend URL
# Set BACKEND_URL to: https://sonora-rest-api.vercel.app
```

### **3. Monitor Performance**
```bash
# Check Vercel analytics
# Monitor function execution times
# Watch for database connection issues
```

## 📱 Vercel Dashboard Features

### **Available in Dashboard**
- ✅ **Environment Variables Management**
- ✅ **Deployment History**
- ✅ **Function Logs**
- ✅ **Performance Analytics**
- ✅ **Domain Management**
- ✅ **Team Collaboration**

### **Recommended Settings**
- **Auto-deploy**: Enable for main branch
- **Preview deployments**: Enable for PRs
- **Function timeout**: Set to 30 seconds
- **Memory**: Use default (1024 MB)

## 🎉 Success Checklist

- [ ] **Environment variables configured**
- [ ] **Database accessible from Vercel**
- [ ] **Deployment successful**
- [ ] **API endpoints responding**
- [ ] **Frontend updated with new backend URL**
- [ ] **OAuth working correctly**
- [ ] **AI services responding**
- [ ] **Stripe integration working**

## 🆘 Need Help?

### **Vercel Support**
- [Vercel Documentation](https://vercel.com/docs)
- [Vercel Community](https://github.com/vercel/vercel/discussions)
- [Vercel Support](https://vercel.com/support)

### **Django + Vercel Resources**
- [Django on Vercel](https://vercel.com/guides/deploying-django-with-vercel)
- [Serverless Django](https://github.com/vercel/vercel/tree/main/examples/django)

---

**Happy Deploying! 🚀**

Your Sonora REST API should now be running on Vercel with all the AI services, OAuth, and subscription-free functionality!
