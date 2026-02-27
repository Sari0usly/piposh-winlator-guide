## 🇮🇱 מדריך להפעלת תמיכה מלאה בעברית בתוך Winlator.

![Android](https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white)
![Winlator](https://img.shields.io/badge/Runtime-Winlator-1f6feb)
![Wine](https://img.shields.io/badge/Powered_by-Wine-red)
![Locale](https://img.shields.io/badge/Locale-he_IL.UTF--8-orange)
![CodePage](https://img.shields.io/badge/CodePage-1255%20%7C%20862-blue)
![License](https://img.shields.io/badge/License-Guide_Only-lightgrey)
![Status](https://img.shields.io/badge/Status-Stable-brightgreen)

מדריך תמיכה בעברית עבור Winlator.  
מיועד לפתרון בעיות קידוד, פונטים ו־RTL בתוך Windows Container.

---

## המדריך פותר

- ג'יבריש (àíë)
- ריבועים □□□ במקום אותיות
- בעיות ANSI בתוכנות ישנות
- קידוד שגוי בעברית
- בעיות RTL חלקיות

---

## שלב 1 – הגדרת Locale

Edit Container → Environment Variables

הוסיפו:

Name:
LC_ALL

Value:
he_IL.UTF-8

שמרו והפעילו מחדש את ה-Container.

---

## שלב 2 – פונטים עבריים

אם מופיעים ריבועים:

1. הפעילו Container
2. כנסו ל:
   C:\Windows\Fonts
3. העתיקו פונטים עבריים (TTF)


⚠️ אין לכלול או לשתף Windows Fonts בתוך הריפו (מוגנים בזכויות יוצרים).

עם זאת, אם יש לכם רישיון חוקי ל-Windows,
מותר להעתיק פונטים מהעותק המקורי המותקן אצלכם
לשימוש אישי בתוך ה-Container.

לחלופין, ניתן להשתמש בפונטים חינמיים כמו:
- Noto Sans Hebrew
- Assistant

---

## שלב 3 – תיקון קידוד (Registry)

הריצו את:

HebrewFix.reg

ולאחר מכן בצעו Restart מלא ל-Container.

---

## מה קובץ ה-Registry מגדיר

- ACP → 1255
- OEMCP → 862
- System Language → 040d (Hebrew)
- Font Substitutes → Arial

---

## תאימות

נבדק על:
- Windows XP Container
- Winlator (גרסה עדכנית בזמן כתיבת המדריך)

ייתכן שיעבוד גם על Containers אחרים, אך לא נבדק רשמית.

---

## 🔬 הגדרות מתקדמות (לא חובה)

## שימוש ב-LANG ו-LC_CTYPE בנוסף ל-LC_ALL

ברוב המקרים מספיק להגדיר:

'LC_ALL=he_IL.UTF-8'

עם זאת, במקרים נדירים בהם תוכנות מתנהגות מוזר (בעיקר ישנות מאוד),
ניתן להוסיף גם:

'LANG=he_IL.UTF-8'
'LC_CTYPE=he_IL.UTF-8'

⚠️ הערה:
LC_ALL כבר עוקף את כל המשתנים האחרים.
אם מוסיפים את שלושתם – ודאו שכולם מוגדרים לאותו ערך,
אחרת עלול להיווצר קונפליקט קידוד.

---

## 🛠 פתרון בעיות מתקדם

## 1️⃣ עדיין יש ג'יבריש

בדקו:

regedit →
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Nls\CodePage

ודאו:
'ACP = 1255' 
'OEMCP = 862'

---

## 2️⃣ טקסט הפוך (RTL שבור)

- ודאו שהפעלתם את קובץ ה-reg.
- נסו להוסיף LC_CTYPE בנוסף ל-LC_ALL.
- בדקו אם התוכנה עצמה תומכת RTL.

במקרים מסוימים Wine לא מממש RTL מלא.

---

## 3️⃣ תוכנה לא נפתחת אחרי שינוי Locale

- הסירו משתני LANG / LC_CTYPE.
- השאירו רק LC_ALL.
- בצעו Restart מלא.

---

## 4️⃣ פונטים מותקנים אך עדיין ריבועים

- בדקו שהקבצים אכן בפורמט TTF.
- בצעו Restart ל-Container.
- בדקו Font Substitutes ברג'יסטרי.

---

## 5️⃣ בעיות ב-Windows XP בלבד

אם משהו מתנהג מוזר:
נסו ליצור Container חדש ולהחיל את השלבים מחדש.

---

## הערות

- יש להחיל בכל Container חדש.
- נבדק על Windows XP.
- מומלץ Restart מלא לאחר כל שינוי מערכת.

---

תמיכה מלאה בעברית ל-Winlator • פשוט לשימוש
