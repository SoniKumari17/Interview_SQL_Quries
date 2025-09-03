### 40. What is the difference between DELETE and TRUNCATE statements?
The TRUNCATE command is used to delete all the rows from the table and free the space containing the table.
The DELETE command deletes only the rows from the table based on the condition given in the where clause or deletes all the rows from the table if no condition is specified. But it does not free the space containing the table

#### Explantions :
##### 1. DELETE

Jab hum DELETE use karte hain, toh rows table se delete ho jaati hain.

Lekin table ke liye allocated space (storage) free nahi hota.

Matlab rows chali gayi, par unke jagah ka pointer DBMS ke paas abhi bhi reserve hai future insert ke liye.

Example:

Tumhare paas 100 rows hain.

Tumne DELETE FROM students; chalaya.

Ab table empty hai (0 rows), par table ki memory space 100 rows jitni reserved hai.

Agar tum dobara insert karogi toh woh wahi jagah use karega.

#### 2. TRUNCATE

Jab TRUNCATE use karte ho, toh rows delete ho jaati hain aur saath hi table ke liye reserved space bhi free ho jaata hai.

Matlab DBMS ko lagta hai ki ab ye table bilkul naya bana hai.

Example:

Tumhare paas 100 rows hain.

Tumne TRUNCATE TABLE students; chalaya.

Ab table empty hai aur uski memory space bhi free kar di gayi hai.

Next insert karogi toh woh bilkul naye table jaisa behave karega (auto-increment counters bhi reset ho jaate hain).

Step 1: Table banate hain
```sql
CREATE TABLE students (
    id INT IDENTITY(1,1),   -- auto-increment id
    name VARCHAR(50)
);
```
Step 2: Data insert karte hain
```sql
INSERT INTO students (name)
VALUES ('Soni'), ('Sakshi'), ('Riya'), ('Amit'), ('Rohan');
```

👉 Ab table me 5 rows hain.
```sql
Step 3: DELETE use karte hain
DELETE FROM students;
```

Ab table empty ho gaya (0 rows).

Lekin space reserved hai (DB ko lagta hai ki yaha 5 rows ke liye memory use hui thi).

Agar ab tum INSERT karogi toh IDs aage se start hongi, jaise 6,7... (kyunki identity reset nahi hoti).

Step 4: TRUNCATE use karte hain
```sql
TRUNCATE TABLE students;
```

Ab table empty ho gaya aur space bhi free ho gayi.

Agar ab INSERT karogi toh ID phir se 1 se start hogi.

Yeh dikhaata hai ki truncate puri memory reset kar deta hai
#### 35. What is Normalization?
Normalization is the process of organizing data in a database to reduce redundancy and avoid inconsistency. It involves creating separate tables for different entities and linking them through relationships, which makes the data structured and flexible
#### 36. What is Denormalization?
Denormalization is the process of intentionally adding redundancy to a normalized database to improve query performance. It reduces the number of joins needed, making queries faster, though some data may be repeated

Explanation
35. Normalization

Normalization ka matlab hai data ko efficiently organize karna.

Iska goal hai:

Redundancy (duplicate data) kam karna

Data inconsistency (conflicting data) avoid karna

Ye tab hota hai jab hum tables ko tod ke logically connect karte hain aur unke beech relationships define karte hain.

Example (Simple):

Pehle: Ek table me student ke naam + address + course + teacher ka naam hai.

Problem: Agar ek teacher multiple students ko padha raha hai, toh teacher ka naam bar-bar repeat hoga → redundancy.

Solution (Normalization): Teacher ko alag table me rakho aur student table me teacher_id se link karo.

Ab data organized aur consistent hai.

💡 Analogy:

Normalization = Kapdon ko almirah me fold karke alag alag shelves me rakhna, taki dhundhna easy ho aur duplicate na ho.

36. Denormalization

Denormalization ka matlab hai thoda redundant data intentionally rakhna, taki queries fast ho jaye.

Jab normalized tables me data bahut tod diya jaata hai, queries join karne me slow ho sakti hain.

Denormalization me kuch tables ko merge karke ya duplicate info rakh kar performance improve karte hain.

Example (Simple):

Normalized: Student table + Teacher table (linked by teacher_id)

Denormalized: Student table me teacher name bhi directly store kar do → queries fast, lekin teacher ka naam duplicate ho sakta hai.

💡 Analogy:

Denormalization = Almirah me frequently used kapde ek hi jagah rakhna, thoda duplicate ho sakta hai, lekin nikalna fast ho jaata hai.
