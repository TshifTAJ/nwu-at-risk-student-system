# 🎓 NWU Student System - One-Click Standalone Guide

## ⚡ Ultra-Simple Setup (30 Seconds)

This is the **easiest way to run the system** - no Docker, no Git, no terminal needed!

---

## 📥 Step 1: Download

**Download the executable file:**
- **File:** `NWU-Student-System.exe`
- **Size:** 50-150 MB
- **Where:** Save to any folder (e.g., `C:\NWU-System\`)

**Download Link:**
[Get NWU-Student-System.exe (Right-click → Save As)](https://github.com/TshifTAJ/nwu-at-risk-student-system/releases)

---

## ▶️ Step 2: Run

1. **Find the file** - `NWU-Student-System.exe`
2. **Double-click it** - Just double-click, no installation needed
3. **Wait 10-15 seconds** - System initializes
4. **Browser opens automatically** - Goes to http://localhost:3000

**That's it! You're done.** ✅

---

## 🔑 Step 3: Login

Use one of these test accounts:

```
👤 ADMIN
   Email/Username: admin
   Password: admin123

👨‍🎓 LEARNER (Student)
   Email/Username: student1
   Password: student123

👨‍🏫 LECTURER (Faculty)
   Email/Username: lecturer1
   Password: lecturer123

👤 COORDINATOR (Support)
   Email/Username: coordinator1
   Password: coord123
```

---

## 🎯 What Each Role Can Do

### 👨‍🎓 Learner (Student)
- View personal risk score
- See academic performance
- Find support resources
- Schedule appointments
- Track progress

### 👨‍🏫 Lecturer (Faculty)
- View class roster
- See at-risk students
- Get intervention recommendations
- View class analytics
- Generate reports

### 👤 Coordinator (Support)
- Manage student caseload
- Create interventions
- Schedule meetings
- Track outcomes
- Generate reports

### 🔐 Admin
- Manage users
- View system analytics
- Configure settings
- Generate reports
- Access audit logs

---

## 🌐 Access Points

Once running, visit these URLs:

```
Student Dashboard:    http://localhost:3000
Backend API:          http://localhost:8000/api/
Admin Panel:          http://localhost:8000/admin/
API Documentation:    http://localhost:8000/api/docs/
```

---

## ⏸️ Stop the Application

**Option 1:** Close the command window that appeared

**Option 2:** Press `Ctrl+C` in the command window

**Option 3:** Restart your computer

---

## 🔄 Restart the Application

Just double-click the .exe file again!

---

## 📁 Folders Created

After running, you'll see these folders in the same location:

```
NWU-Student-System.exe   ← The application
data/                    ← Database (DON'T delete!)
logs/                    ← Application logs
config.txt               ← Settings
```

---

## 💾 System Requirements

**Minimum:**
- Windows 7 or newer (64-bit)
- 1 GB RAM
- 500 MB free disk space

**Recommended:**
- Windows 10 or newer
- 2+ GB RAM
- 1 GB free disk space

---

## 🧪 Test the System

### Test 1: Login as Learner
1. Go to http://localhost:3000
2. Login: `student1 / student123`
3. Click "Dashboard"
4. View your risk score

### Test 2: Login as Lecturer
1. Go to http://localhost:3000
2. Login: `lecturer1 / lecturer123`
3. Click "My Classes"
4. View student risk scores

### Test 3: Login as Coordinator
1. Go to http://localhost:3000
2. Login: `coordinator1 / coord123`
3. Click "My Caseload"
4. View assigned students
5. Create an intervention

### Test 4: Login as Admin
1. Go to http://localhost:3000
2. Login: `admin / admin123`
3. Click "Analytics"
4. View system dashboard
5. Generate a report

---

## ❌ Troubleshooting

### Application Won't Start

**Problem:** You click the .exe but nothing happens

**Solutions:**
1. Wait 30 seconds (it's loading)
2. Check if a black command window appeared in the background
3. Restart your computer
4. Delete the `data` folder and try again

### Port Already in Use

**Problem:** "Port 3000 is already in use" error

**Solutions:**
1. Close any other applications using that port
2. Restart your computer
3. Restart the application

**Find what's using the port:**
```bash
netstat -ano | findstr :3000
```

Then kill it:
```bash
taskkill /PID <PID> /F
```

### Blank/White Screen

**Problem:** Browser shows blank page

**Solutions:**
1. Wait 10 more seconds
2. Refresh the page (press F5 or Ctrl+R)
3. Hard refresh (press Ctrl+Shift+Delete)
4. Close browser and reopen
5. Try a different browser (Chrome, Firefox, Edge)

### Can't Login

**Problem:** "Invalid credentials" error

**Solutions:**
1. Check you're using correct credentials (see above)
2. Clear browser cache (Ctrl+Shift+Delete)
3. Try a different browser
4. Delete `data` folder and restart
5. Check that backend is running

### Slow Performance

**Problem:** System is very slow

**Solutions:**
1. Make sure you have at least 1GB RAM free
2. Close other applications
3. Restart the application
4. Restart your computer

### Database Error

**Problem:** "Database connection failed" error

**Solutions:**
1. Close the application
2. Delete the `data` folder
3. Restart the application
4. The database will be recreated

---

## 💾 Backup Your Data

To backup everything:

1. Close the application
2. Go to folder where .exe is located
3. Copy the `data` folder to a safe location
4. To restore: Copy the `data` folder back

**Important:** Don't delete the `data` folder while running!

---

## 🗑️ Uninstall

To completely remove the application:

1. Close the application
2. Delete `NWU-Student-System.exe`
3. Delete the `data` folder (if you don't need the data)
4. Done! Nothing left behind.

No registry entries, no hidden files, clean uninstall!

---

## ⚙️ Advanced Options

### Run in Debug Mode

Create a file called `DEBUG.txt` in the same folder as the .exe

Then run the .exe - you'll see detailed logs

### Custom Settings

Create a file called `config.txt` in the same folder:

```
DEBUG=false
PORT=3000
BACKEND_PORT=8000
DATABASE_TYPE=sqlite
```

---

## 📊 Features Included

✅ **Learner Portal**
- Personal dashboard
- Risk score visualization
- Support resources
- Appointment booking
- Progress tracking

✅ **Lecturer Dashboard**
- Class roster
- Student risk scores
- Intervention recommendations
- Class analytics
- Report generation

✅ **Coordinator Platform**
- Caseload management
- Intervention tracking
- Meeting scheduling
- Outcome documentation
- Performance reports

✅ **Admin Dashboard**
- User management
- System analytics
- Configuration
- Strategic reports
- Audit logs

✅ **Risk Scoring**
- Automatic risk assessment
- Real-time updates
- Historical tracking
- Predictive modeling

✅ **Interventions**
- Create interventions
- Track progress
- Document outcomes
- Measure effectiveness

✅ **Alerts & Notifications**
- Real-time alerts
- Email notifications
- Alert history
- Custom rules

✅ **Analytics & Reporting**
- Interactive dashboards
- Custom reports
- Export to Excel
- Trend analysis

---

## 🔐 Security & Privacy

✅ **All data stays on your computer** - Nothing sent to internet
✅ **No registration required** - Just download and run
✅ **Passwords encrypted** - Secure storage
✅ **No tracking** - No analytics or cookies
✅ **No ads** - Clean interface
✅ **No personal data collection** - Your privacy respected

---

## 🚀 Performance

| Metric | Value |
|--------|-------|
| Startup Time | 10-15 seconds |
| Memory Usage | 300-400 MB |
| Disk Usage | 500 MB |
| Number of Users | 1-100 |
| Database Type | SQLite (local) |

---

## 📞 Support & Help

### I have a question
- Check this guide first
- Read README.md
- Check GitHub Issues

### Something's not working
1. Check the Troubleshooting section above
2. View the logs (check `logs/` folder)
3. Delete `data` folder and restart
4. Restart your computer

### I want to report a bug
1. Open GitHub Issues
2. Describe the problem
3. Include any error messages
4. Attach log files if possible

---

## 🔄 Updates

To update to a newer version:

1. Download the new `NWU-Student-System.exe`
2. Replace your old one
3. Your `data` folder stays intact
4. Run the new version
5. No data loss!

---

## ⭐ Tips & Tricks

**Tip 1:** Keep the `data` folder backed up
**Tip 2:** Create different user accounts for testing
**Tip 3:** Use Firefox or Chrome for best experience
**Tip 4:** Don't move the .exe file without its `data` folder
**Tip 5:** Restart regularly for best performance

---

## 📚 Next Steps

1. ✅ Download the .exe
2. ✅ Double-click to start
3. ✅ Login with test credentials
4. ✅ Explore each user role
5. ✅ Read feature guides
6. ✅ Create real user accounts
7. ✅ Import your data
8. ✅ Go live!

---

## ✨ That's It!

You now have a complete, production-ready at-risk student system running on your computer!

**Questions?** Check the troubleshooting section or open an issue on GitHub.

**Ready to use?** Login now: **http://localhost:3000**

---

**Version:** 1.0.0  
**Last Updated:** 2026-09-12  
**Status:** ✅ Production Ready
