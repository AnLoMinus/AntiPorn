# 🚀 התחלה מהירה (Getting Started)

מדריך זה יעזור לך להתקין ולהשתמש ב-AntiPorn תוך מספר דקות.

## 📋 דרישות מוקדמות

- מערכת הפעלה: Linux, macOS, או Windows
- הרשאות מנהל (sudo/administrator)
- גישה לטרמינל/שורת פקודה

## 📥 התקנה

### שיטה 1: התקנה אוטומטית (מומלץ)

1. **הורד את המאגר**:
```bash
git clone https://github.com/AnLoMinus/AntiPorn.git
cd AntiPorn
```

2. **הרץ את הסקריפט**:
```bash
chmod +x AntiPorn
./AntiPorn
```

3. **בחר אפשרות 'a'** להתקנה אוטומטית

### שיטה 2: התקנה ידנית

1. **גיבוי hosts קיים**:
```bash
sudo cp /etc/hosts /etc/hosts_old
```

2. **הוספת רשימת החסימה**:
```bash
sudo cat PornHosts >> /etc/hosts
```

## ✅ אימות ההתקנה

לאחר ההתקנה, נסה לגשת לאתר פורנו ידוע. אם ההתקנה הצליחה, האתר לא יטען.

## 🔧 פלטפורמות ספציפיות

### Linux
התהליך זהה להתקנה הכללית. ודא שיש לך הרשאות sudo.

### macOS
1. פתח Terminal
2. עקוב אחר ההוראות הכלליות
3. ייתכן שתצטרך לאפשר הרשאות בטיחות במערכת ההפעלה

### Windows
1. לחץ ימני על Notepad → "Run as administrator"
2. פתח: `C:\Windows\System32\drivers\etc\hosts`
3. העתק את תוכן `PornHosts` לסוף הקובץ
4. שמור ואתחל מחדש

## ⚠️ אזהרות חשובות

- **גיבוי**: תמיד גבה את קובץ hosts המקורי לפני שינויים
- **אל תכבה**: לאחר ההתקנה, אל תכבה את מנגנון החסימה
- **עדכונים**: עקוב אחר עדכונים לרשימת האתרים

## 🔄 הסרת התקנה

להסרת ההתקנה:
```bash
sudo cp /etc/hosts_old /etc/hosts
```

או ב-Windows, הסר את השורות שהוספת מקובץ ה-hosts.

## 📚 המשך

לאחר ההתקנה, קרא את:
- [מדריך שימוש מפורט](USAGE.md)
- [שאלות נפוצות](FAQ.md)
- [פתרון בעיות](TROUBLESHOOTING.md)

## 🆘 בעיות?

אם נתקלת בבעיות:
1. קרא את [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
2. פתח [Issue](https://github.com/AnLoMinus/AntiPorn/issues) חדש

---

**תודה על השימוש ב-AntiPorn!** 🙏

