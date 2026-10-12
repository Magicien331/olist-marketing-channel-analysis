<div dir="rtl">

# הנתונים

## קובצי המקור שמורים במאגר עצמו

כל מה שנמצא בתיקייה `data/raw` מנוהל ב-git ונכלל במאגר. אחרי שכפול של המאגר הנתונים כבר נמצאים במקום:

<div dir="ltr">

```
git clone https://github.com/Magicien331/olist-marketing-channel-analysis.git
```

</div>

אין שלב הורדה ואין צורך בחשבון Kaggle כדי לעבוד על הפרויקט. הקובץ <code dir="ltr">.gitignore</code> אינו מכיל שום כלל על `data/raw`, וזה מכוון, כדי ששכפול של המאגר יביא גם את הנתונים. על תיקיית הפלטים `data/clean` כן קיים כלל, ולפיו רק קבצים ששמם מתחיל ב-<code dir="ltr">final_</code> נשמרים במאגר.

התיקייה `data/clean` מחזיקה את הטבלאות המעובדות שנוצרות במחברות. מחברת 02 כותבת אליה שלושה קבצים, וכולם נוצרים מחדש בכל הרצה:

| קובץ | שורות | תוכן |
|---|---|---|
| <code dir="ltr">final_deals.csv</code> | 842 | עסקה, ערוץ, מועד חתימה, ימי חשיפה עד סוף הנתונים, כשירות לחלון והאם הופעלה |
| <code dir="ltr">final_sellers.csv</code> | 341 | מוכרים מעסקאות כשירות: שלושת רכיבי הציון, ההכנסות בחלון ומחוצה לו, והציון הסופי |
| <code dir="ltr">final_channels.csv</code> | 8 | לידים, עסקאות, שיעורי המרה והפעלה ורווחי סמך |

**אין לערוך את הקבצים האלה ביד.** ההרצה הבאה של המחברת תדרוס כל שינוי כזה, ולכן כל תיקון נעשה בקוד.

## מקורות

חברת Olist פרסמה באתר Kaggle שני מאגרים ציבוריים. **שימו לב להבדל ביניהם:** מאגר משפך השיווק מצהיר שהלידים שבו נדגמו אקראית מתוך כלל הלידים, בעוד שמאגר המסחר אינו מתואר כמדגם.

| מקור | שם המאגר ב-Kaggle | מספר קבצים |
|---|---|---|
| Brazilian E-Commerce Public Dataset by Olist | `olistbr/brazilian-ecommerce` | 9 |
| Marketing Funnel by Olist | `olistbr/marketing-funnel-olist` | 2 |

הקבצים הורדו באמצעות הספרייה [kagglehub](https://pypi.org/project/kagglehub/), גרסה 2 של כל מאגר, והועתקו ישירות לתיקייה `data/raw` בלי תת-תיקיות. שני קבצים, טבלת הביקורות וטבלת תרגום הקטגוריות, מגיעים עם סיומות שורה של Windows, והם נשמרים בדיוק כך.

**רישיון.** שני המאגרים, [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) ו-[Marketing Funnel by Olist](https://www.kaggle.com/datasets/olistbr/marketing-funnel-olist), פורסמו על ידי חברת Olist ברישיון [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/), שמתיר שימוש לא מסחרי, עם ייחוס ובשיתוף בתנאים זהים. הקבצים בתיקייה `data/raw` הם עותק שלהם, והקבצים בתיקייה `data/clean` נגזרים מהם, ולכן שניהם כפופים לאותו רישיון.

## הקבצים בתיקייה `data/raw`

**מתוך `olistbr/brazilian-ecommerce`**, צד הפלטפורמה: מה שהמוכרים עשו בפועל.

| קובץ | גודל | תוכן |
|---|---|---|
| `olist_orders_dataset.csv` | <span dir="ltr">17&nbsp;MB</span> | שורה לכל הזמנה, עם סטטוס וחותמות זמן |
| `olist_order_items_dataset.csv` | <span dir="ltr">15&nbsp;MB</span> | שורות פריט, מקשרות הזמנות למוכרים ומכילות מחיר ומשלוח |
| `olist_order_payments_dataset.csv` | <span dir="ltr">5.5&nbsp;MB</span> | אמצעי תשלום, תשלומים וסכום לכל הזמנה |
| `olist_order_reviews_dataset.csv` | <span dir="ltr">14&nbsp;MB</span> | ציוני ביקורת ותגובות לכל הזמנה |
| `olist_customers_dataset.csv` | <span dir="ltr">8.6&nbsp;MB</span> | מזהי לקוחות ומיקום |
| `olist_sellers_dataset.csv` | <span dir="ltr">171&nbsp;KB</span> | מזהי מוכרים ומיקום |
| `olist_products_dataset.csv` | <span dir="ltr">2.3&nbsp;MB</span> | מאפייני מוצר וקטגוריה |
| `olist_geolocation_dataset.csv` | <span dir="ltr">58&nbsp;MB</span> | רשימת נקודות ציון, ולא טבלת חיפוש. יש בה כפילויות רבות וצריך לצמצם אותה לפני שימוש |
| `product_category_name_translation.csv` | <span dir="ltr">2.6&nbsp;KB</span> | שמות קטגוריות, מפורטוגזית לאנגלית |

**מתוך `olistbr/marketing-funnel-olist`**, צד הגיוס: מאיפה הגיעו המוכרים.

| קובץ | גודל | תוכן |
|---|---|---|
| `olist_marketing_qualified_leads_dataset.csv` | <span dir="ltr">687&nbsp;KB</span> | הלידים, כולל ערוץ המקור |
| `olist_closed_deals_dataset.csv` | <span dir="ltr">167&nbsp;KB</span> | לידים שהפכו למוכרים, מחברים את המשפך לטבלת המוכרים |

סך הכול 11 קבצים, כ-121 מגהבייט.

## תיעוד הטבלאות

הקובץ `DATA_SCHEMA.pdf` שבתיקיית הבסיס מתעד את כל 11 הטבלאות: מה כל טבלה מכילה, מה המשמעות של שורה בודדת בה, כל העמודות והמפתחות, הקשרים בין הטבלאות, והמלכודות שכדאי להכיר לפני שכותבים פעולת join בקוד. כדאי לקרוא אותו לפני שמתחילים לעבוד על הנתונים.

## הערה על גודל הקבצים

הקובץ `olist_geolocation_dataset.csv` שוקל 58 מגהבייט. GitHub מציג אזהרה על קבצים מעל 50 מגהבייט אבל מקבל אותם, והסף שמעליו GitHub דוחה את הקובץ הוא 100 מגהבייט. לכן אין צורך להשתמש ב-Git LFS לצורך כך.

</div>
