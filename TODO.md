# TODO — Link2Maps

---

## להתחיל מחר

- [ ] **ליצור API key חדש** ב-Google Cloud Console
  - Credentials → + Create credentials → API Key
  - להגביל ל: Maps JavaScript API + Places API
  - לבטל את ה-comment בתחתית `index.html` ולהכניס את המפתח
  - לעדכן גם את `PHOTO_BASE` בראש ה-script
- [ ] לבדוק שהמפה עולה ותמונות הכרטיסים נטענות אחרי חיבור המפתח

---

## פתוח

- [ ] מחיקת מקום שמור — אין כרגע אפשרות למחוק מ-localStorage
- [ ] מקומות שנוספו ללא API key (keyless) לא יהפכו ל-markers כשהמפה תחזור — דורש פתרון (re-lookup?)
- [ ] הוספת כפתור "הצג מפה" במובייל (המפה מוסתרת לחלוטין)
- [ ] תמיכה בלימה 🇵🇪 — כרגע כל החיפושים מוסיפים "New York" כברירת מחדל

---

## הסתיים

- [x] chat-bar קבוע בתחתית המסך (`position: fixed; bottom: 0`)
- [x] שורת קלט פשוטה: `[שדה] [🔍]` בלבד — הוסרו 📎 ו-▾
- [x] auto-detect URL בשדה הראשי (מעבר אוטומטי לטאב לינק)
- [x] טאב "לינק לסרטון" — חילוץ כותרת אוטומטי ללא שדה נוסף
- [x] כפתור "לא, שנה" בשלב האישור
- [x] placeholder: "הוסף מיקום או הדבק לינק"
- [x] שמירת מקומות ב-localStorage (שורדים רענון)
- [x] הוספת מקומות ללא API key — URL ישיר ל-Maps
- [x] תיקון iOS auto-zoom (font-size 16px על inputs)
- [x] תיקון mobile layout: html height, overflow-x, min-width על cards
- [x] הסרת תמונות שבורות — fallback לאמוג'י קטגוריה
- [x] תיקון קטגוריות — הוסר "show"/"music" מבידור, תוקן `\bbar\b`
- [x] פאנל מפה נשמר עם placeholder, מוכן לחיבור עתידי
- [x] selection-bar ממוקם מעל ה-chat-bar
- [x] תמיכה מלאה במובייל (one-column, ללא מפה, safe-area)
