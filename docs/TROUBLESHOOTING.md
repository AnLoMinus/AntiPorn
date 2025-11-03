# 🔧 פתרון בעיות (Troubleshooting)

מדריך זה עוזר לפתור בעיות נפוצות בעת שימוש ב-AntiPorn.

## 🚨 בעיות התקנה

### שגיאה: "Permission denied"
**בעיה**: אין הרשאות להרצת הסקריפט.

**פתרון**:
```bash
chmod +x AntiPorn
```

### שגיאה: "sudo: command not found"
**בעיה**: אין גישה ל-sudo או הרשאות מנהל.

**פתרון**:
- Windows: הרץ PowerShell כמנהל
- Linux/macOS: ודא שיש לך הרשאות sudo או הרץ כמשתמש root

### שגיאה: "No such file or directory: PornHosts"
**בעיה**: קובץ `PornHosts` לא נמצא.

**פתרון**:
```bash
ls -la  # בדוק שהקובץ קיים
pwd     # ודא שאתה בתיקייה הנכונה
```

## 🌐 בעיות חסימה

### אתרים עדיין נטענים

**פתרון 1: ניקוי מטמון DNS**

macOS:
```bash
sudo dscacheutil -flushcache
sudo killall -HUP mDNSResponder
```

Linux:
```bash
sudo systemd-resolve --flush-caches
# או
sudo service network-manager restart
```

Windows:
```cmd
ipconfig /flushdns
```

**פתרון 2: אימות ההתקנה**
```bash
grep "0.0.0.0" /etc/hosts | head -5
```

אם אין פלט, ההתקנה לא הצליחה.

**פתרון 3: אתחול מחדש**
לפעמים צריך לאתחל את המחשב כדי שהשינויים ייכנסו לתוקף.

### חלק מהאתרים חסומים וחלק לא

**סיבה**: האתרים שלא חסומים לא נמצאים ברשימה.

**פתרון**: הוסף אותם ידנית ל-`PornHosts` או בקש הוספה דרך Issue.

### כל האתרים חסומים (כולל לגיטימיים)

**סיבה**: ייתכן שהרשימה רחבה מדי או שיש שגיאה בקובץ hosts.

**פתרון**:
```bash
sudo cp /etc/hosts_old /etc/hosts  # החזר גיבוי
```

ואז התקן מחדש בצורה זהירה יותר.

## 🔄 בעיות עדכון

### git pull לא עובד

**פתרון**:
```bash
git status  # בדוק אם יש שינויים מקומיים
git stash   # שמור שינויים מקומיים
git pull    # עדכן
```

### קונפליקטים בקובץ hosts

**פתרון**:
```bash
# גבה את hosts הנוכחי
sudo cp /etc/hosts /etc/hosts_backup_$(date +%Y%m%d)

# החזר גיבוי מקורי והתקן מחדש
sudo cp /etc/hosts_old /etc/hosts
./AntiPorn
```

## 💻 בעיות פלטפורמה ספציפיות

### macOS - לא יכול לערוך /etc/hosts

**פתרון**:
1. ודא שאתה משתמש ב-sudo
2. בדוק הרשאות בטיחות ב-System Preferences → Security
3. נסה לערוך דרך TextEdit עם הרשאות מנהל:
   ```bash
   sudo open -a TextEdit /etc/hosts
   ```

### Windows - לא יכול לשמור את hosts

**פתרון**:
1. הרץ Notepad **כמנהל** (Right-click → Run as administrator)
2. פתח את הקובץ דרך Notepad (לא דרך double-click)
3. שמור את הקובץ

### Linux - בעיות עם systemd-resolve

**פתרון**:
```bash
# עבור מערכות ישנות יותר:
sudo /etc/init.d/networking restart
```

## 🐛 בעיות בסקריפט

### הסקריפט קופא/לא מגיב

**פתרון**: 
- לחץ Ctrl+C כדי לעצור
- בדוק את הודעות השגיאה
- הרץ עם debug:
  ```bash
  bash -x AntiPorn
  ```

### שגיאות בקוד הצבעים

**סיבה**: הטרמינל לא תומך בצבעים.

**פתרון**: זה לא משפיע על הפונקציונליות, רק על התצוגה. אפשר להתעלם.

## 📝 בעיות עם קבצים

### קובץ hosts גדול מדי

**פתרון**: זה תקין. קובץ hosts יכול להיות גדול מאוד (עד כמה מאות MB).

### לא יכול למצוא hosts_old

**פתרון**: 
```bash
# חפש קבצי גיבוי:
ls -la /etc/hosts*
ls -la ~/hosts*
```

אם אין, תצטרך לשחזר ידנית או להתקין מחדש.

## 🔐 בעיות הרשאות

### "Operation not permitted" ב-macOS

**פתרון**:
1. System Preferences → Security & Privacy
2. אפשר גישה לטרמינל/פקודות
3. נסה שוב

### לא יכול להריץ sudo

**פתרון**:
- ודא שאתה במערכת ההרשאות של sudo
- עבור Windows, השתמש ב-Administrator

## 📞 קבלת עזרה נוספת

אם אף פתרון לא עזר:

1. **אסוף מידע**:
   ```bash
   uname -a                    # מידע על המערכת
   cat /etc/hosts | wc -l      # מספר שורות ב-hosts
   ls -la AntiPorn PornHosts   # קבצים
   ```

2. **צור Issue**:
   - פתח [Issue חדש](https://github.com/AnLoMinus/AntiPorn/issues)
   - כלול את המידע שאספת
   - תאר את הבעיה בפירוט

3. **בדוק Issues קיימים**:
   - אולי הבעיה כבר דווחה ונפתרה

---

**זכור**: רוב הבעיות נפתרות עם גיבוי נכון והבנה בסיסית של המערכת.

