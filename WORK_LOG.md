# Work Log — Link2Maps

---

## 2026-05-25 — סיכום עבודה

### 1. מה שינינו היום
- **הסרת תלות ב-Google Maps API** לשלב ההוספה — חיפוש מקומות עובד כעת ללא API key, בעזרת בניית URL ישיר (`google.com/maps/search/?api=1&query=...`)
- **שיפור מובייל מקיף**: תיקון iOS auto-zoom (font-size 16px על inputs), html height, overflow-x
- **פישוט שורת הקלט**: הוסרו כפתור 📎 (image upload), כפתור ▾ (expand), וטאב "תמונה" לחלוטין
- **טאב "לינק לסרטון"**: מוציא כותרת אוטומטית מהסרטון דרך noembed, ללא שדה קלט נוסף
- **כפתור "לא, שנה"** בשלב האישור — מחזיר את השם לעריכה
- **שמירה ב-localStorage** — מקומות שמורים ונטענים מחדש בכל רענון
- **placeholder** עודכן ל-"הוסף מיקום או הדבק לינק"
- תיקון באג: `openPanel()` ניסה לגשת לאלמנט שנמחק
- הסרת CSS מת של כפתורים שהוסרו

### 2. אילו קבצים עודכנו
- `index.html` — כל השינויים לעיל (3 commits נפרדים)

### 3. מה עובד כרגע
- הוספת מקום (טקסט / לינק לסרטון) — ללא API key, מייצר לינק Maps ישיר
- שמירה ב-`localStorage` — מקומות שורדים רענון דפדפן
- שורת קלט נקייה: `[שדה] [🔍]` בלבד
- אישור / דחייה של תוצאת חיפוש
- auto-detect URL (מעבר אוטומטי לטאב לינק)
- mobile layout תקין — אין zoom אוטומטי ב-iOS
- פאנל מפה נשמר בקוד עם placeholder, מוכן לחיבור API key עתידי
- קארטיסים עם placeholder אמוג'י כשאין תמונה (API key לא תקף)
- הסתרת link-box במובייל

### 4. מה נשאר פתוח
- API key של Google Maps — עדיין לא מוגדר, תמונות כרטיסים לא נטענות
- המפה לא מוצגת (ממתינה ל-API key)
- מקומות שנוספו ללא API key אין להם קואורדינטות → לא יופיעו כ-markers כשהמפה תופעל
- אין אפשרות למחוק מקום שנשמר

### 5. הצעד הבא למחר
- **ליצור API key חדש** ב-Google Cloud Console (Maps JavaScript API + Places API)
- לפתוח את השורה המוקומנטת בתחתית `index.html`:
  `<!-- <script src="https://maps.googleapis.com/.../js?key=YOUR_API_KEY..."> -->`
- לעדכן גם את `PHOTO_BASE` בראש ה-script
- לבדוק שהמפה עולה ותמונות נטענות

---

## 2026-05-24 — סיכום עבודה

### 1. מה שינינו היום
- **הושלמה** החלפת ה-FAB + overlay ב-`chat-bar` קבוע בתחתית המסך
- הקובץ `index.html` נכתב מחדש במלואו דרך Bash (עקיפת בעיית "file modified since read" של VSCode)
- ווידג'ט הצ'ט פעיל: שורת קלט תמיד גלויה + פאנל שנפתח מעלה
- הוספת תמיכה מלאה למובייל (map-panel מוסתר, גלילה רגילה, `safe-area-inset-bottom`)
- המשתמשת החלה בתהליך יצירת Google Maps API key חדש בפרויקט Link2Maps ב-Google Cloud Console

### 2. אילו קבצים עודכנו
- `index.html` — גרסה סופית עם chat-bar קבוע, החלפה מלאה של FAB + overlay

### 3. מה עובד כרגע
- chat-bar קבוע בתחתית (`position: fixed; bottom: 0`)
- 4 טאבים: שם / לינק / תמונה / הדבק
- auto-detect URL בשדה הראשי (מעבר אוטומטי לטאב לינק)
- כפתור 📎 → מעבר לטאב תמונה + file picker
- Enter → שליחה
- פאנל נפתח מעלה (max 56vh) עם אנימציה
- selection-bar ממוקם מעל ה-chat-bar (`bottom: calc(66px + 16px)`)
- תמיכה מובייל: one-column, ללא מפה, safe-area
- כל הפונקציונליות הקיימת שמורה (מפה, מרקרים, קארדים, חיפוש, אישור הוספה)
- **ממתין לעדכון API key** — המפתח הנוכחי עשוי להיות פג/מוגבל

### 4. מה נשאר פתוח
- לסיים יצירת ה-API key החדש ולעדכן אותו ב-`index.html` (3 מקומות)
- לבדוק בדפדפן: desktop + mobile אחרי עדכון המפתח

### 5. הצעד הבא למחר
- לסיים יצירת ה-API key ב-Google Cloud Console → Credentials → + Create credentials → API Key
- להגביל את המפתח: Maps JavaScript API + Places API
- לעדכן ב-`index.html`: `API_KEY`, `PHOTO_BASE`, ושורת ה-`<script>` התחתונה

---

## 2026-05-23 — סיכום עבודה

### 1. מה שינינו היום
- ניסיון להחליף את ה-FAB (כפתור +) ואת ה-agent-overlay המודאלי בוידג'ט צ'ט קבוע בתחתית המסך
- תוכנן ועוצב מחדש הממשק כולו: `chat-bar` קבוע, `chat-panel-wrap` שנפתח למעלה, שורת קלט תמיד גלויה עם כפתורי 📎 / ▾ / 🔍
- הוספת תמיכה מלאה במובייל (media query, הסתרת מפה, `min-height: 100dvh`)
- כתיבת לוגיקת auto-detect URL, switchTab, openPanel/closePanel
- **הקובץ נמצא כרגע בגרסת ביניים** — FAB עם hover-bar שמתרחב + overlay — לא הגרסה הסופית
- הניסיונות לכתוב את הגרסה הסופית נכשלו בשל שגיאת "file modified since read" (VSCode ערך את הקובץ בין הקריאות)

### 2. אילו קבצים עודכנו
- `index.html` — גרסת ביניים: FAB עם hover quick-input, overlay קיים, **לא** chat-bar קבוע

### 3. מה עובד כרגע
- 3 קארדים עם מפה, מרקרים ו-infowindow
- FAB פותח overlay עם 4 טאבים (שם / לינק / תמונה / הדבק)
- חיפוש Google Places, תצוגת תוצאה, אישור הוספה
- העתקת לינקים, בחירה מרובה (selection bar)
- hover bar על ה-FAB מציג שדה קלט מהיר

### 4. מה נשאר פתוח
- **המשימה העיקרית**: להחליף FAB + overlay ב-chat-bar קבוע בתחתית
- chat-bar מתוכנן: `position:fixed; bottom:0; left:0; right:0` עם panel שנפתח מעלה
- תמיכה מלאה במובייל (הסתרת map-panel, גלילה רגילה, safe-area)
- selection-bar צריך להיות `bottom: calc(var(--bar-h) + 16px)` כדי לא לחפוף את ה-chat-bar

### 5. הצעד הבא למחר
- לפתוח את `index.html` ב-VSCode, לסגור שמירה אוטומטית / prettier אם פועל
- להריץ את הכתיבה מחדש עם הגרסה המלאה שתוכננה (כבר מוכנה)
- לאמת בדפדפן: desktop (מפה + קארדים + chat-bar), mobile (רק קארדים + chat-bar)

---
