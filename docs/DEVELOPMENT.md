# 💻 מדריך פיתוח (Development Guide)

מדריך זה מיועד למפתחים הרוצים לתרום לפרויקט AntiPorn.

## 🚀 הגדרת סביבת פיתוח

### דרישות מוקדמות

- Git
- Shell (bash/sh)
- עורך קוד (VSCode, Vim, וכו')
- גישה למערכת Linux/macOS לבדיקות

### התקנה

1. **Clone המאגר**:
```bash
git clone https://github.com/AnLoMinus/AntiPorn.git
cd AntiPorn
```

2. **צור branch לפיתוח**:
```bash
git checkout -b dev/your-feature-name
```

3. **הגדר Git hooks** (אופציונלי):
```bash
chmod +x .git/hooks/pre-commit  # אם יש
```

## 📝 סגנון קוד

### Shell Scripts

- **הזחה**: 2 רווחים
- **שמות משתנים**: UPPERCASE עבור קבועים, lowercase עבור משתנים
- **פונקציות**: snake_case
- **הערות**: הסבר מה הקוד עושה

**דוגמה**:
```bash
#!/bin/sh
# Function to backup hosts file
backup_hosts() {
  echo "# Backing up hosts file"
  sudo cp /etc/hosts /etc/hosts_old
}
```

### Markdown

- **כותרות**: השתמש בהיררכיה נכונה (# ## ###)
- **רשימות**: 2 רווחים להזחה
- **קישורים**: תיאור ברור

## 🧪 בדיקות

### בדיקות ידניות

1. **בדיקת הסקריפט**:
```bash
bash -n AntiPorn  # בדיקת syntax
bash -x AntiPorn  # הרצה עם debug
```

2. **בדיקת hosts**:
```bash
# ודא שהפורמט נכון
head -10 PornHosts | grep "^0\.0\.0\.0"
```

3. **בדיקת תיעוד**:
```bash
# ודא שאין קישורים שבורים ב-Markdown
```

### בדיקות אוטומטיות

הפרויקט משתמש ב-GitHub Actions לבדיקות אוטומטיות:
- Lint של Markdown
- בדיקת Shell Scripts
- בדיקת מבנה קבצים

## 🔄 תהליך פיתוח

### 1. יצירת Feature חדש

```bash
# צור branch
git checkout -b feature/new-feature

# עבד על השינויים
# ...

# Commit
git commit -m "feat: add new feature"

# Push
git push origin feature/new-feature
```

### 2. תיקון Bug

```bash
# צור branch
git checkout -b fix/bug-description

# תיקון
# ...

# Commit
git commit -m "fix: fix bug description"

# Push
git push origin fix/bug-description
```

### 3. שיפור תיעוד

```bash
# צור branch
git checkout -b docs/improvement

# עדכן תיעוד
# ...

# Commit
git commit -m "docs: improve documentation"
```

## 📋 Commit Messages

השתמש ב-Conventional Commits:

- `feat:` - תכונה חדשה
- `fix:` - תיקון באג
- `docs:` - שינוי תיעוד
- `style:` - שינוי עיצוב (לא משפיע על קוד)
- `refactor:` - שינוי קוד (לא משנה פונקציונליות)
- `test:` - הוספת/שינוי בדיקות
- `chore:` - משימות תחזוקה

**דוגמה**:
```
feat: add automatic update feature
fix: resolve hosts backup issue
docs: update installation guide
```

## 🔍 Code Review

לפני פתיחת Pull Request:

1. **עצמך Review**:
   - האם הקוד עובד?
   - האם יש הערות מספיקות?
   - האם התיעוד מעודכן?

2. **בדוק Style**:
   - האם הקוד עוקב אחר הסגנון?
   - האם אין שגיאות lint?

3. **בדוק תיעוד**:
   - האם README מעודכן?
   - האם CHANGELOG מעודכן?

## 🐛 Debugging

### כלים שימושיים

```bash
# בדיקת syntax
bash -n script.sh

# הרצה עם trace
bash -x script.sh

# בדיקת משתנים
echo $VARIABLE

# בדיקת הרשאות
ls -la /etc/hosts
```

### Logging

הוסף הודעות ברורות:
```bash
echo "# Starting installation..."
echo "# Backup completed successfully!"
echo "ERROR: Something went wrong!"
```

## 📦 בניית Release

1. **עדכן CHANGELOG.md**
2. **עדכן גרסה** (אם יש version file)
3. **צור Tag**:
```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
```

## 🤝 תרומה

לפני פתיחת PR:

1. ודא שהקוד עובד
2. עדכן תיעוד
3. כתוב commit messages ברורים
4. עקוב אחר התבנית ב-PULL_REQUEST_TEMPLATE.md

## 📚 משאבים

- [CONTRIBUTING.md](../CONTRIBUTING.md) - מדריך תרומה כללי
- [Shell Scripting Guide](https://www.shellscript.sh/)
- [Markdown Guide](https://www.markdownguide.org/)

---

**תודה על התרומה לפרויקט!** 🙏

